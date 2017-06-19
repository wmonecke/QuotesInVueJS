<template lang="html">
  <div class="container">

    <div v-on:click="eraseQuote(i)" class="oneQuote" v-for="(quote, i) in myQuotes">
      <p>Quote #{{ i + 1 }}: {{ quote }} </p>
    </div>
  </div>
</template>

<script>
  import { eventBus } from '../main.js'

  export default {
    data: function() {
      return {
        myQuotes: [
          '"The greater danger for most of us lies not in setting our aim too high and falling short, but in setting our aim too low, and achieving our mark."'
        ]
      }
    },

    created: function () {
      eventBus.$on('addedNewQuote', (myNewQuote) => {
        if (this.myQuotes.length === 10) {
          console.log('No more quotes can be added. Sorry.');
          return;
        }
        console.log('Quote can be added.');
        this.myQuotes.push(myNewQuote);
      });
    },

    methods: {
      eraseQuote: function(index) {
        this.myQuotes.splice(index, 1);
        eventBus.$emit('deletedQuote', index);
      }
    }
  }
</script>

<style lang="css" scoped>
  .container {
    padding: 50px;

    height: 20vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .oneQuote {
    cursor: pointer;
    border: 1px solid lightblue;
    border-radius: 10px;
    width: 300px;
    padding: 10px;
    transition: background-color .5s ease;
    margin: 10px;
    font-family: cursive;
  }
  .oneQuote:hover {
    background-color: tomato;
  }
</style>

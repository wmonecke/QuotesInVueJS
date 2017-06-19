<template lang="html">
  <div class="container">
    <div class="centerContainer">
      <h4> Quote: </h4>
    </div>

    <div class="centerContainer">
      <textarea
      rows="8"
      cols="80"
      placeholder="Write your quote here."
      v-model:value="myQuote"
      ></textarea>
    </div>

    <button class="button" v-on:click="addQuote"> Add a Quote </button>
  </div>
</template>


<script>
  import { eventBus } from '../main.js'

  export default {
    data: function() {
      return {
        myQuote: ''
      }
    },


    methods: {
      addQuote: function() {
        eventBus.$emit('addedNewQuote', this.myQuote);
      }
    }
  }
</script>


<style lang="css" scoped>
  .container {
    position: relative;
  }
  .centerContainer {
    display: flex;
    align-items: center;
    justify-content: center;
  }
  textarea {
    resize: none;
    outline: none;
    width: 400px;
    height: 100px;
    margin-bottom: 10px;
  }
  .button {
    outline: none;
    border-radius: 4px;
    display: block;
    border: 1px solid black;
    margin: auto;
    width: 200px;
    transition: background-color .5s ease;
  }

  .button:hover {
    background-color: tomato;
  }
</style>

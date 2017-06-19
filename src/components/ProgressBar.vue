<template lang="html">
  <div class="container">

    <h2> Quotes Added: </h2>

    <div class="barContainer">
      <div class="bar" v-bind:style="{width: progress + '%'}"></div>
    </div>

  </div>
</template>


<script>
  import { eventBus } from '../main.js'

  export default {
    data: function() {
      return {
        progress: 10
      }
    },

    created: function() {
      eventBus.$on('addedNewQuote', () => {
        if (this.progress === 100) {
          console.log('No more quotes. Treshold reached.')
          return
        }
        console.log('Treshold not reached. Quote added to ProgressBar')
        this.progress += 10;
      });

      eventBus.$on('deletedQuote', (index) => {
        if(this.progress === 0) return;
        this.progress -= 10;
      });
    }
  }
</script>


<style lang="css" scoped>

  .barContainer {
    border: 1px solid lightgrey;
    width: 100%;
    border-radius: 5px;
  }

  .bar {
    border-radius: 4px;
    background-color: lightblue;
    height: 5vh;
    width: 0%;
    box-sizing: border-box;
    transition: width .5s ease;
  }

</style>

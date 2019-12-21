<template>
  <div class="guessword">
    <div class="blankwordslots"
         v-for="letter in blankword" :key="letter">{{letter}}</div>
  </div>
</template>

<script>
export default {
  name: 'BlankWordSlots',
  props: ['blankword']
}
</script>

<style scoped>
  .blankwordslots {
    display: inline-block;
    border-bottom: 2px solid #345;
    width: 30px;
    height: 30px;
    margin: 3px;
    text-align: center;
    text-transform: uppercase;
    font-size: 24px;
    vertical-align: bottom;
  }
</style>

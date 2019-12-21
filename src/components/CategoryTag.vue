<template>
    <h2>{{ch}}</h2>
</template>

<script>
export default {
  name: 'CategoryTag',
  props: ['category', 'gameState'],
  data: function () {
    return {
      ch: ''
    }
  },
  watch: {
    gameState: function () {
      if (this.gameState === 'win') {
        this.ch = 'Congratulations you win! Play again.'
      } else if (this.gameState === 'lose') {
        this.ch = "You're dead kid! Try again."
      } else if (this.gameState === '') {
        this.ch = 'The category is ' + this.category
      }
    }
  }
}

</script>

<style scoped>

</style>

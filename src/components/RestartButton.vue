<template>
    <div class="restart">
      <button class="restartbutton" :hidden="!gameOver" @click="clicked">Play Again</button>
    </div>
</template>

<script>
export default {
  name: 'RestartButton',
  props: ['gameOver'],
  methods: {
    clicked () {
      this.$emit('restart')
    }
  }
}
</script>

<style scoped>
.restartbutton {
  background-color: black;
  color: #fff;
  font-size: 20px;
  height: 40px;
  border: none;
  border-radius: 4px;
  margin: 0px;
}
.restartbutton:hover {
  background-color: dodgerblue;
}
.restartbutton:disabled {
  opacity: .5%;
}
</style>

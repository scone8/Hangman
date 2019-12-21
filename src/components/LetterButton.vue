<template>
  <button class="letterbutton" :id="letter" :disabled="disabled" @click="clicked">{{letter}}</button>
</template>

<script>
export default {
  name: 'LetterButton',
  props: ['letter', 'gameOver'],
  data: function () {
    return {
      disabled: false
    }
  },
  methods: {
    clicked () {
      this.disabled = true
      this.$emit('letter-clicked')
    }
  },
  watch: {
    gameOver: function (newValue) {
      this.disabled = newValue
    }
  }
}
</script>

<style scoped>
  .letterbutton {
    background-color: black;
    color:#fff;
    font-size: 20px;
    width: 40px;
    height: 40px;
    border: none;
    border-radius: 4px;
    margin: 1px;
  }

  .letterbutton:hover {
    background-color: dodgerblue;
  }

  .letterbutton:disabled{
    opacity: 0.5;
  }
</style>

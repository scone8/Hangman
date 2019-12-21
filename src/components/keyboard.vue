<template>
  <div class="keyboard">
    <div v-for="row in letters" :key="row" class="keyboard-row" >
      <LetterButton v-for="letter in row" :letter="letter" :key="letter" :gameOver="gameOver" @letter-clicked="checkletter(letter)"></LetterButton>
    </div>
  </div>
</template>

<script>
import LetterButton from '@/components/LetterButton'

export default {
  name: 'keyboard',
  props: ['gameOver'],
  data: function () {
    return {
      letters: [['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I'],
        ['J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q'],
        ['R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z']]
    }
  },
  components: {LetterButton},
  methods: {
    checkletter (letter) {
      this.$emit('checklet', letter)
    }
  },
  watch: {
    gameOver: function () {
      LetterButton.disabled = false
    }
  }
}
</script>

<style scoped>
.class{
  margin-top: 500px
}
</style>

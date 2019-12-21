<template>
  <img :src="sources[strikes]" class="hangman-picture"/>
</template>

<script>
export default {
  name: 'HangmanImage',
  props: ['strikes'],
  data: function () {
    return {
      sources: [require('../assets/hangman-0.png'),
        require('../assets/hangman-1.png'),
        require('../assets/hangman-2.png'),
        require('../assets/hangman-3.png'),
        require('../assets/hangman-4.png'),
        require('../assets/hangman-5.png'),
        require('../assets/hangman-6.png'),
        require('../assets/hangman-7.png'),
        require('../assets/hangman-8.png'),
        require('../assets/hangman-9.png'),
        require('../assets/animals.png')]
    }
  }
}
</script>

<style scoped>
.hangman-picture{
  border: none;
  border-radius: 25px;
  height: 225px;
  margin-bottom:40px;
  margin-top:40px;
}
</style>

 <template>
  <div id="app">
    <img src="./assets/logo2.png" id="logo">
    <br>
    <CategoryTag :category="category" :gameState="gameState"/>
    <br>
    <BlankWordSlots :blankword="blankword" :key="blankword"/>
    <br>
    <HangmanImage :strikes="strikes"/>
    <br>
    <Keyboard :gameOver="gameOver" @checklet="checkletter"/>
    <br>
    <br>
    <RestartButton :gameOver="gameOver" @restart="restart" />
  </div>
</template>

<script>
import Keyboard from '@/components/keyboard'
import BlankWordSlots from '@/components/BlankWordSlots'
import HangmanImage from '@/components/HangmanImage'
import Word from '@/Words'
import CategoryTag from '@/components/CategoryTag'
import RestartButton from '@/components/RestartButton'

export default {
  name: 'App',
  components: {
    RestartButton,
    CategoryTag,
    BlankWordSlots,
    Keyboard,
    HangmanImage
  },
  data: function () {
    return {
      gameOver: false,
      gameState: 'win',
      guessword: '',
      words: [],
      category: '',
      blankword: [],
      c: 0,
      strikes: 0
    }
  },
  methods: {
    random (min, max) {
      return Math.floor(Math.random() * (max + 1)) + min
    },
    getRandomWord () {
      this.words = Word[this.random(0, Word.length + 1)]
      this.category = this.words[0]
      this.guessword = this.words[1]
    },
    checkletter (letter) {
      if (!this.gameOver) {
        var lowerletter = letter.toLowerCase()
        var correctGuess = false
        for (var i = 0; i < this.guessword.length; i++) {
          if (lowerletter === this.guessword[i]) {
            var upperletter = lowerletter.toUpperCase()
            this.$set(this.blankword, i, upperletter)
            correctGuess = true
            this.c++
          }
        }
        if (this.c === this.guessword.length) {
          this.gameOver = true
          this.gameState = 'win'
          this.strikes = 10
        }
        if (!correctGuess) {
          this.strikes++
        }
        if (this.strikes === 9) {
          this.gameOver = true
          this.gameState = 'lose'
          for (var j = 0; j < this.guessword.length; j++) {
            this.$set(this.blankword, j, this.guessword[j])
          }
        }
      }
    },
    converttoblank () {
      for (var i = 0; i < this.guessword.length; i++) {
        this.blankword.push('')
      }
    },
    restart () {
      this.gameOver = false
      this.c = 0
      this.strikes = 0
      this.gameState = ''
      this.words = []
      this.category = ''
      this.blankword = []
      this.lose = false
      this.getRandomWord()
      this.converttoblank()
    }
  },
  mounted () {
    this.gameState = ''
    this.getRandomWord()
    this.converttoblank()
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 25px;
}
#logo{
    height: 100px;
    width: auto;
}
</style>

<template>

  <img alt="Vue logo" src="./assets/logo.png">
  <h1>
    Prospect Reaction Timer
  </h1>
  <p>
    <button @click="startGame" >PLAY</button>
  </p>


  <div class="play-area">
    <div class="results" v-show="!boxShowing">
      <Results>
        <p>Reaction Time - {{ score }} ms</p>
        <p>{{ comment }}</p>
      </Results>
    </div>
    <div class="game" v-show="boxShowing">
      <Game  @shot="stopGame"/>
    </div>
  </div>

</template>

<script>
import Game from './components/Game.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
    Game,
    Results
  },
  data() {
    return {
      startTime: 0,
      stopTime: 0,
      score: 0,
      boxShowing: false,
      comment: ""
    }
  },
  methods: {
    startGame() {
      setTimeout(() => {
        this.boxShowing = !this.boxShowing
        const current = new Date
        this.startTime = current.getTime()
      }, 1000);
    },
    stopGame() {
      this.boxShowing = !this.boxShowing
      const current = new Date
      this.stopTime = current.getTime()
      this.score = this.stopTime - this.startTime
      if (this.score > 500) {
        this.comment = "fat fingers"
      } else if (this.score > 300) {
        this.comment = "i see you've been practising"
      } else {
        this.comment = "you're worthy"
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.play-area {
  margin-top: 4rem;
}

button {
  border: none;
  border-radius: 50px;
  background: #42b983;
  color: #fff;
  font-size: 1.3rem;
  font-weight: bolder;
  padding: 0.5rem 1rem;
  cursor: pointer;
  transition: 0.5s ease-in-out;
}

button:focus {
  outline: none;
}

img {
  width: 100px;
}

.results p:nth-child(2) {
  color: #2c3e50;
  font-weight: bolder;
  font-size: 1.3rem;
}

</style>

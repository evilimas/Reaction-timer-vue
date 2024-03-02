<template>
  <h1>Reaction Timer</h1>
  <p>Want to check your reaction time?</p>
  <button class="how-to" @click="toggleModal">How To Play</button>
  <button @click="start" :disabled="isPlaying">Press Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResults" :score="score" />
  <div v-if="showModal">
    <Modal @close="toggleModal" />
  </div>
</template>

<script>
import Block from './components/Block.vue';
import Results from './components/Results.vue';
import Modal from './components/Modal.vue';

export default {
  name: 'App',
  components: { Block, Results, Modal },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
      showModal: false,
    };
  },
  methods: {
    start() {
      this.delay = 1000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #1d1d1d;
  margin-top: 60px;
}
body {
  background: #c4c4c4;
}
button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 9px 16px;
  border-radius: 6px;
  font-size: 20px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.4;
  cursor: not-allowed;
}
.how-to {
  position: absolute;
  top: 0;
  right: 20%;
}
</style>

<template>
  <div class="top-container">
    <h1>Reaction Timer</h1>
    <p>Want to check your reaction time?</p>
    <button class="how-to" @click="toggleModal">How To Play</button>
  </div>
  <button @click="start" :disabled="isPlaying">Press Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResults" :score="score" />
  <div v-if="showModal">
    <Modal @close="toggleModal" />
  </div>
  <Footer />
</template>

<script>
import Block from './components/Block.vue';
import Results from './components/Results.vue';
import Modal from './components/Modal.vue';
import Footer from './components/Footer.vue';

export default {
  name: 'App',
  components: { Block, Results, Modal, Footer },
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
  margin: 0;
  background: #c4c4c4;
}
h1 {
  font-size: 3em;
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
button:hover {
  background: #18c096;
}
.how-to {
  position: absolute;
  top: 0;
  right: 20%;
}
.top-container {
  padding-top: 3.5em;
}
.top-container p {
  font-size: 1.3em;
}
</style>

<template>
  <h4>
    Your Reaction Time is: <span> {{ score }} </span>ms
  </h4>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  props: ['score'],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = 'Ninja Fingers';
    } else if (this.score < 400) {
      this.rank = 'Fast Reflexes';
    } else {
      this.rank = 'Pretty Slow...';
    }
  },
};
</script>

<style>
span {
  color: #0faf87;
}
.rank {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
</style>

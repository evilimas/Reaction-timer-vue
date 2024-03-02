<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal">
      <h1>How to Play</h1>
      <div class="content">
        <ol>
          <li>Press Play Button</li>
          <li>Wait for the green Block to Apear</li>
          <li>Press on it as quickly as posible!</li>
          <li>See the results in milliseconds</li>
        </ol>
      </div>
      <h3>Not satisfied with results?</h3>
      <p>Try again</p>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    closeModal() {
      this.$emit('close');
    },
  },
};
</script>

<style>
.modal {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
}
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.479);
  width: 100%;
  height: 100%;
}
.modal h1 {
  color: rgb(4, 77, 77);
  border: none;
  padding: 0;
}
.modal p {
  font-style: normal;
}
.content {
  text-align: left;
}
</style>

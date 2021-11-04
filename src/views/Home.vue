<template>
  <div class="container">
    <h2>Change Query String</h2>
    <div class="input">
      <label for="">Enter a fruit name: </label>
      <input type="text" v-model.lazy="fruit" />
    </div>
    <div v-if="correctAnswer">
      <p class="message">{{ message }}</p>
    </div>
    <div class="btn">
      <button @click="changeQueryString">Update Query String</button>
      <button @click="removeQueryString">Remove Query String</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  components: {},
  data() {
    return {
      fruit: "",
      correctAnswer: null,
      message: "🍏apple",
    };
  },
  methods: {
    changeQueryString() {
      this.$router.replace({ query: { fruit: this.fruit.toLowerCase() } });
    },
    removeQueryString() {},
  },
  watch: {
    $route() {},
  },
};
</script>

<style>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
}

.btn {
  display: flex;
  gap: 10px;
  margin-top: 20px;
}

.message {
  padding: 20px;
  font-size: 2rem;
  font-weight: bold;
  letter-spacing: 2px;
}
</style>
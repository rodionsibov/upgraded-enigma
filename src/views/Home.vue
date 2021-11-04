<template>
  <div class="container">
    <h1>Change Query String</h1>
    <div class="input">
      <label for="">Enter a fruit name: </label>
      <input type="text" v-model="fruit" />
    </div>
    <div v-if="correctAnswer">
      <p class="message">{{ this.message }}</p>
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
      message: "",
    };
  },
  methods: {
    changeQueryString() {
      this.$router.replace({ query: { fruit: this.fruit.toLowerCase() } });
      this.fruit = "";
    },
    removeQueryString() {
      this.$router.replace({ name: "Home" });
      this.fruit = "";
    },
  },
  watch: {
    $route() {
      if (this.$route.query.fruit === "apple") {
        this.correctAnswer = !this.correctAnswer;
        this.message = "Congrats, you found the lucky fruit!";
      }
      // } else {
      //   this.correctAnswer = null;
      // }
    },
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
  margin-top: 10px;
}

.message {
  padding: 20px;
  margin: 0;
  font-size: 1.5rem;
  font-weight: bold;
  color: #42b983;
}

input {
  display: block;
  font-size: 2rem;
  padding: 10px;
  margin: 10px auto;
  width: 90%;
}
</style>
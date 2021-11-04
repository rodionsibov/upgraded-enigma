<template>
  <div class="container">
    <h1>Change Query String</h1>
    <div>
      <label for="">Enter a fruit name: </label>
      <input type="text" v-model="fruit" />
    </div>
    <div v-if="correctAnswer">
      <p class="message">{{ this.message }}</p>
    </div>
    <div class="buttons">
      <button class="btn-large" @click="changeQueryString">
        Update Query String
      </button>
      <button class="btn-large" @click="removeQueryString">
        Remove Query String
      </button>
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
      } else {
        this.correctAnswer = null;
      }
    },
  },
};
</script>

<style>
.buttons {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-top: 20px;
}

.message {
  font-size: 1.5rem;
  font-weight: bold;
  color: tomato;
}
</style>
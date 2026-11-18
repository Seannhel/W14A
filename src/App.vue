
<template>
  <div class="app">
    <h1>😂 Joke Generator</h1>

    <button @click="getJoke()">New Joke</button>

    <NormalJokeButton @normal="mode = 'normal'" />
    <button @click="mode = 'loud'">Loud Joke</button>
    <button @click="mode = 'snake'">Snake Joke</button>

    <JokeDisplay :joke="joke" :mode="mode" />

    <JokeSearch @search="getJoke" />
  </div>
</template>

<script>
import axios from "axios";
import JokeDisplay from "./components/JokeDisplay.vue";
import JokeSearch from "./components/JokeSearch.vue";
import NormalJokeButton from "./components/NormalJokeButton.vue";

export default {
  components: {
    JokeDisplay,
    JokeSearch,
    NormalJokeButton
  },

  data() {
    return {
      joke: null,
      mode: "normal"
    };
  },

  methods: {
    async getJoke(word = "") {
      try {
        const res = await axios.get(
          "https://v2.jokeapi.dev/joke/Any",
          { params: { contains: word, "safe-mode": "" } }
        );

        if (res.data.error) {
          alert("No joke found!");
          return;
        }

        this.joke = res.data;
        this.mode = "normal";
      } catch (error) {
        alert("Could not load joke!");
      }
    }
  },

  mounted() {
    this.getJoke();
  }
};
</script>

<style>
body {
  font-family: Arial, sans-serif;
  text-align: center;
  background: #eef2ff;
}

.app {
  background: white;
  max-width: 650px;
  margin: 50px auto;
  padding: 30px;
  border-radius: 15px;
}

button {
  background: royalblue;
  color: white;
  padding: 10px 15px;
  margin: 5px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background: darkblue;
}

input {
  padding: 10px;
  margin: 5px;
}
</style>

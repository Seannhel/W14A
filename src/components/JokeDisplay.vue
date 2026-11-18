
<template>
  <div v-if="joke">
    <TwoPartSnakeJoke
      v-if="joke.type === 'twopart' && mode === 'snake'"
      :joke="joke"
    />

    <div v-else>
      <h3>{{ change(joke.setup || joke.joke) }}</h3>
      <p v-if="joke.delivery">
        {{ change(joke.delivery) }}
      </p>
    </div>
  </div>
</template>

<script>
import TwoPartSnakeJoke from "./TwoPartSnakeJoke.vue";

export default {
  components: { TwoPartSnakeJoke },
  props: ["joke", "mode"],

  methods: {
    change(text) {
      if (this.mode === "loud") return text.toUpperCase();
      if (this.mode === "snake") return text.replace(/ /g, "_");
      return text;
    }
  }
};
</script>

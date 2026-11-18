
<template>
  <div>
    <h3>{{ snake(joke.setup) }}</h3>
    <p>{{ snake(joke.delivery) }}</p>
  </div>
</template>

<script>
export default {
  props: ["joke"],
  methods: {
    snake(text) {
      return text.replace(/ /g, "_");
    }
  }
};
</script>

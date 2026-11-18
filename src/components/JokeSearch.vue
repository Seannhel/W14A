
<template>
  <div>
    <input v-model="word" placeholder="Search a joke" />
    <button @click="$emit('search', word)">Search</button>
  </div>
</template>

<script>
export default {
  emits: ["search"],
  data() {
    return { word: "" };
  }
};
</script>

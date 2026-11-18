
<template>
  <button @click="$emit('normal')">Normal Joke</button>
</template>

<script>
export default {
  emits: ["normal"]
};
</script>

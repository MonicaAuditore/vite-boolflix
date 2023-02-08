<script>
export default {
  name: "AppSearch",
  data() {
    return {};
  },
  props: {
    message: String,
  },
};
</script>

<template>
  <h1>{{ message }}</h1>
  <button @click="$emit('eventodalfiglio', 'tvb', 5)">Invia al padre</button>
</template>

<style scoped></style>

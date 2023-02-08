<script>
import { store } from "../store";

export default {
  name: "AppSearch",
  data() {
    return {
      store,
    };
  },
  props: {
    message: String,
  },

  methods: {
    incrementa() {
      this.store.counter++;
    },
  },
};
</script>

<template>
  <button @click="incrementa">btn search</button>
  <h2>search {{ store.counter }}</h2>
  <h1>{{ message }}</h1>
  <button @click="$emit('eventodalfiglio', 'tvb', 5)">Invia al padre</button>
</template>

<style scoped></style>

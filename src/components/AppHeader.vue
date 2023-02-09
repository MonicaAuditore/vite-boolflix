<script>
import { store } from "../store";

export default {
  name: "AppHeader",

  data() {
    return {
      store,
    };
  },

  methods: {},
};
</script>

<template>
  <div>
    <input type="text" v-model="store.searchText" placeholder="cerca" />
    <button @click="$emit('performSearch')">search</button>
  </div>
</template>

<style scoped></style>

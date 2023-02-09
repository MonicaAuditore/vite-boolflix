<script>
import { store } from "../store";

export default {
  name: "AppMain",
  data() {
    return {
      store,
    };
  },
  props: {},

  methods: {},
};
</script>

<template>
  <main>
    <div v-for="movie in store.movies">
      <h1>{{ movie.title }}</h1>
      <h2>{{ movie.original_title }}</h2>
      <h3>{{ movie.original_language }}</h3>
      <h4>{{ movie.vote_average }}</h4>
    </div>
  </main>
</template>

<style scoped></style>

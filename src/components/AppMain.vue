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

  methods: {
    getFlag(lang) {
      if (lang == "en") {
        lang = "uk";
      } else if (lang == "pt") {
        lang = "po";
      }

      const flag = `https://www.worldometers.info//img/flags/small/tn_${lang}-flag.gif`;

      return flag;
    },
  },
};
</script>

<template>
  <main>
    <div v-for="movie in store.movies">
      <h2>{{ movie.title }}</h2>
      <h5>{{ movie.original_title }}</h5>
      <img :src="getFlag(movie.original_language)" />
      <p>{{ movie.original_language }}</p>
      <p>{{ movie.vote_average }}</p>
    </div>
  </main>
</template>

<style scoped></style>

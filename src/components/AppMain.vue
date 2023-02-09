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
      } else if (lang == "es") {
        lang = "sp";
      }

      const flag = `https://www.worldometers.info//img/flags/small/tn_${lang}-flag.gif`;

      return flag;
    },

    getImage(img) {
      let url = "https://image.tmdb.org/t/p/" + "w342" + img;
      return url;
    },
  },
};
</script>

<template>
  <main>
    <h2>Film</h2>
    <div v-for="movie in store.movies">
      <img :src="getImage(movie.poster_path)" />
      <h2>{{ movie.title }}</h2>
      <h5>{{ movie.original_title }}</h5>
      <img :src="getFlag(movie.original_language)" />
      <p>{{ movie.original_language }}</p>
      <p>{{ movie.vote_average }}</p>
    </div>
    <h2>Serie TV</h2>
    <div v-for="singleSeries in store.series">
      <img :src="getImage(singleSeries.poster_path)" />
      <h2>{{ singleSeries.name }}</h2>
      <h5>{{ singleSeries.original_name }}</h5>
      <img :src="getFlag(singleSeries.original_language)" />
      <p>{{ singleSeries.original_language }}</p>
      <p>{{ singleSeries.vote_average }}</p>
    </div>
  </main>
</template>

<style scoped></style>

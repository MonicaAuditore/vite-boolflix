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

    calcoloVoto(voto) {
      let votoUno = (voto / 10) * 100;
      let votoDue = (votoUno / 100) * 5;
      votoDue = Math.round(votoDue);
      return votoDue;
    },
  },
};
</script>

<template>
  <main>
    <div class="filmList">
      <div class="titleFilms">
        <h2>Film</h2>
      </div>
      <div class="allFilms">
        <div v-for="movie in store.movies">
          <img :src="getImage(movie.poster_path)" />
          <h2>{{ movie.title }}</h2>
          <h5>{{ movie.original_title }}</h5>
          <img :src="getFlag(movie.original_language)" />
          <!-- <p>{{ movie.original_language }}</p> -->
          <div>
            <span v-for="votoSingolo in calcoloVoto(movie.vote_average)">
              ★
            </span>
            <span v-for="votoSingolo in 5 - calcoloVoto(movie.vote_average)">
              ☆
            </span>
          </div>
        </div>
      </div>
    </div>

    <div class="seriesList">
      <div class="seriesTitle">
        <h2>Serie TV</h2>
      </div>
      <div class="allSeries">
        <div v-for="singleSeries in store.series">
          <img :src="getImage(singleSeries.poster_path)" />
          <h2>{{ singleSeries.name }}</h2>
          <h5>{{ singleSeries.original_name }}</h5>
          <img :src="getFlag(singleSeries.original_language)" />
          <!-- <p>{{ singleSeries.original_language }}</p> -->
          <div>
            <span v-for="votoSingolo in calcoloVoto(singleSeries.vote_average)">
              ★
            </span>
            <span
              v-for="votoSingolo in 5 - calcoloVoto(singleSeries.vote_average)"
            >
              ☆
            </span>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
.allFilms {
  display: flex;
}

.allSeries {
  display: flex;
}
</style>

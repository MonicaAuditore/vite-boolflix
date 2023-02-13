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

      if (img == null) {
        let url =
          "https://upload.wikimedia.org/wikipedia/commons/3/3f/Placeholder_view_vector.svg";
      }

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
        <h2 class="genere">Film</h2>
      </div>
      <div class="allFilms">
        <div v-for="movie in store.movies">
          <div class="cardFilm">
            <div class="cardFilmImg">
              <img
                class="imgCopertineFilm"
                :src="getImage(movie.poster_path)"
              />
            </div>
            <div class="datiFilm">
              <div class="datiInner">
                <h2>{{ movie.title }}</h2>
                <h5>{{ movie.original_title }}</h5>
                <img class="flag" :src="getFlag(movie.original_language)" />
                <!-- <p>{{ movie.original_language }}</p> -->
                <div>
                  <span v-for="votoSingolo in calcoloVoto(movie.vote_average)">
                    ★
                  </span>
                  <span
                    v-for="votoSingolo in 5 - calcoloVoto(movie.vote_average)"
                  >
                    ☆
                  </span>
                </div>
                <p>{{ movie.overview }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="seriesList">
      <div class="seriesTitle">
        <h2 class="genere">Serie TV</h2>
      </div>
      <div class="allSeries">
        <div v-for="singleSeries in store.series">
          <div class="cardSerie">
            <div class="cardSerieImg">
              <img
                class="imgCopertineSeries"
                :src="getImage(singleSeries.poster_path)"
              />
            </div>
            <div class="datiSerie">
              <div class="datiInner">
                <h2>{{ singleSeries.name }}</h2>
                <h5>{{ singleSeries.original_name }}</h5>
                <img
                  class="flag"
                  :src="getFlag(singleSeries.original_language)"
                />
                <!-- <p>{{ singleSeries.original_language }}</p> -->
                <div>
                  <span
                    class="star"
                    v-for="votoSingolo in calcoloVoto(
                      singleSeries.vote_average
                    )"
                  >
                    ★
                  </span>
                  <span
                    v-for="votoSingolo in 5 -
                    calcoloVoto(singleSeries.vote_average)"
                  >
                    ☆
                  </span>
                </div>
                <p>{{ singleSeries.overview }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped></style>

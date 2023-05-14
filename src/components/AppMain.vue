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
    // Questo metodo restituisce l'URL della bandiera del paese corrispondente alla lingua specificata

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
    // Questo metodo restituisce l'URL dell'immagine di copertina del film o della serie TV

    getImage(img) {
      let url = "https://image.tmdb.org/t/p/" + "w342" + img;

      if (img == null) {
        let url =
          "https://upload.wikimedia.org/wikipedia/commons/3/3f/Placeholder_view_vector.svg";
      }

      return url;
    },
    // Questo metodo calcola il punteggio di valutazione (voto) e lo converte in una scala da 1 a 5

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
        <!-- Ciclo attraverso tutti i film nell'array "store.movies" -->

        <div v-for="movie in store.movies">
          <div class="cardFilm">
            <div class="cardFilmImg">
              <!-- Immagine di copertina del film -->

              <img
                class="imgCopertineFilm"
                :src="getImage(movie.poster_path)"
              />
            </div>
            <div class="datiFilm">
              <div class="datiInner">
                <!-- Titolo e titolo originale del film -->

                <h2>{{ movie.title }}</h2>
                <h5>{{ movie.original_title }}</h5>
                <!-- Bandiera corrispondente alla lingua originale del film -->

                <img class="flag" :src="getFlag(movie.original_language)" />
                <!-- Punteggio di valutazione del film -->
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
      <!-- Sezione delle serie TV -->

      <div class="seriesTitle">
        <h2 class="genere">Serie TV</h2>
      </div>
      <div class="allSeries">
        <!-- Ciclo attraverso tutte le serie TV nell'array "store.series" -->

        <div v-for="singleSeries in store.series">
          <div class="cardSerie">
            <div class="cardSerieImg">
              <!-- Immagine di copertina della serie TV -->

              <img
                class="imgCopertineSeries"
                :src="getImage(singleSeries.poster_path)"
              />
            </div>
            <div class="datiSerie">
              <div class="datiInner">
                <!-- Nome e nome originale della serie TV -->

                <h2>{{ singleSeries.name }}</h2>
                <h5>{{ singleSeries.original_name }}</h5>
                <!-- Bandiera corrispondente alla lingua originale della serie TV -->

                <img
                  class="flag"
                  :src="getFlag(singleSeries.original_language)"
                />
                <!-- Punteggio di valutazione della serie TV -->

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
                <!-- Trama della serie TV -->

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

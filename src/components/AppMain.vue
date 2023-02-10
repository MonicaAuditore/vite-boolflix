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
              <h2>{{ singleSeries.name }}</h2>
              <h5>{{ singleSeries.original_name }}</h5>
              <img
                class="flag"
                :src="getFlag(singleSeries.original_language)"
              />
              <!-- <p>{{ singleSeries.original_language }}</p> -->
              <div>
                <span
                  v-for="votoSingolo in calcoloVoto(singleSeries.vote_average)"
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
            </div>
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

.imgCopertineFilm {
  height: 507px;
  object-fit: cover;
}

.imgCopertineSeries {
  height: 507px;
  object-fit: cover;
}

.allFilms,
.allSeries {
  overflow-y: auto;
  padding-bottom: 65px;
}

.allFilms::-webkit-scrollbar,
.allSeries::-webkit-scrollbar {
  width: 10px;
}

.allFilms::-webkit-scrollbar-thumb,
.allSeries::-webkit-thumb {
  background-color: #303030;
  border-radius: 10px;
}

.allFilms::-webkit-scrollbar-track,
.allSeries::-webkit-scrollbar-track {
  -webkit-box-shadow: inset 0 0 5px rgba(102, 102, 102, 0.3);
}

.filmList {
  padding: 100px 0px;
  background-color: #141414;
}

.seriesList {
  background-color: #141414;
}

input {
  padding: 10px;
  border-radius: 20px;
  padding-right: 100px;
  background-color: #ffffffd4;
}

button {
  padding: 10px 20px;
  border-radius: 20px;
  cursor: pointer;
}

.cardFilm,
.cardSerie {
  position: relative;
}

.datiFilm,
.datiSerie {
  opacity: 0;
  position: absolute;
  bottom: 0;
  left: 0;
  padding: 30px;
  width: 100%;

  background-image: linear-gradient(
    to top,
    #000000,
    #000000e7,
    #000000cb,
    #000000a6,
    #00000000
  );
}

.cardFilm:hover .datiFilm,
.cardSerie:hover .datiSerie {
  opacity: 1;
  transition: all 0.7s;
}

.genere {
  padding: 28px;
}

h2,
h5 {
  color: #ffffffd4;
}

h5 {
  padding-top: 20px;
}

.flag {
  width: 40px;
  padding-top: 15px;
}
</style>

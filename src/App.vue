<script>
import axios from "axios";

import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import { store } from "./store";

export default {
  name: "App",
  components: { AppHeader, AppMain },

  data() {
    return {
      store,
      defaultSearchQuery: "adventure",
    };
  },

  methods: {
    // Questo metodo viene chiamato quando si verifica l'evento di ricerca dal componente AppHeader, effettua 2 richieste una per film e una per serie
    handleSearchEvent() {
      axios
        .get("https://api.themoviedb.org/3/search/" + "movie", {
          params: {
            api_key: "6d4cd5494f9ef676c380214313faaad7",
            query: this.store.searchText,
            language: "it-IT",
          },
        })
        .then((response) => {
          console.log(response);
          // Salva i film nella proprietà "movies" dell'oggetto store con i dati della risposta
          this.store.movies = response.data.results;
        });

      axios
        .get("https://api.themoviedb.org/3/search/" + "tv", {
          params: {
            api_key: "6d4cd5494f9ef676c380214313faaad7",
            query: this.store.searchText,
            language: "it-IT",
          },
        })
        .then((response) => {
          console.log(response);
          // Salva le serie TV nella proprietà "series" dell'oggetto store con i dati della risposta
          this.store.series = response.data.results;
        });
    },
  },
  created() {
    this.store.searchText = this.defaultSearchQuery;
    this.handleSearchEvent();
  },
};
</script>

<template>
  <AppHeader @performSearch="handleSearchEvent" />
  <AppMain />
</template>

<style lang="scss">
@use "./styles/main.scss" as *;
</style>

<script>
import SearchBar from "./components/SearchBar.vue";
import AppCard from "./components/AppCard.vue";
import axios from "axios";

export default {
  data() {
    return {
      films: [],
    };
  },

  components: {
    SearchBar,
    AppCard,
  },

  methods: {
    fetchResults(query) {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "9662f4631b63862b49fb1bf5e49bd400",
            query: query,
          },
        })
        .then((results) => {
          this.films = results.data.results;
          console.log(this.films);
        });
    },
  },
};
</script>

<template>
  <SearchBar @fetch-results="fetchResults" />
  <div
    v-if="films.length"
    class="container-fluid films"
  >
    <h2>Films</h2>
    <div class="row">
      <div class="col">
        <div v-for="film in films">
          <AppCard :film="film" />
        </div>
      </div>
    </div>
  </div>

  <div v-else>
    <h2>Inizia la ricerca</h2>
  </div>
</template>

<style lang="scss" scoped></style>

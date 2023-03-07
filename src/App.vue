<script>
import SearchBar from "./components/SearchBar.vue";
import AppCard from "./components/AppCard.vue";
import axios from "axios";

export default {
  data() {
    return {
      films: [],
      tvSeries: [],
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

      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: {
            api_key: "9662f4631b63862b49fb1bf5e49bd400",
            query: query,
          },
        })
        .then((results) => {
          this.tvSeries = results.data.results;
          console.log(this.tvSeries);
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
          <AppCard
            :title="film.title"
            :originalTitle="film.original_title"
            :lang="film.original_language"
            :vote="film.vote_average"
          />
        </div>
      </div>
    </div>
  </div>

  <div
    v-if="tvSeries.length"
    class="container-fluid tv_series"
  >
    <h2>TV Series</h2>
    <div class="row">
      <div class="col">
        <div v-for="tvSeries in tvSeries">
          <AppCard
            :title="tvSeries.name"
            :originalTitle="tvSeries.original_name"
            :lang="tvSeries.original_language"
            :vote="tvSeries.vote_average"
          />
        </div>
      </div>
    </div>
  </div>

  <div v-if="!films.length && !tvSeries.length">
    <div class="container-fluid">
      <h2>Inizia la ricerca</h2>
    </div>
  </div>
</template>

<style lang="scss" scoped></style>

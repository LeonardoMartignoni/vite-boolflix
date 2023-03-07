<script>
import SearchBar from "./components/SearchBar.vue";
import axios from "axios";

export default {
  data() {
    return {
      films: [],
    };
  },

  components: {
    SearchBar,
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
</template>

<style lang="scss" scoped></style>

<script>
import SearchBar from "./components/SearchBar.vue";

export default {
  components: {
    SearchBar,
  },

  methods: {
    fetchResults(query) {
      console.log(query);
    },
  },
};
</script>

<template>
  <SearchBar @fetch-results="fetchResults" />
</template>

<style lang="scss" scoped></style>

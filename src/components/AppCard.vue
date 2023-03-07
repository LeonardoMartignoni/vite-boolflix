<script>
export default {
  data() {
    return {};
  },

  props: {
    film: Object,
  },

  methods: {
    getFlag(code) {
      if (code == "en") return `https://flagcdn.com/w20/gb.png`;
      else if (code == "hy") return `https://flagcdn.com/w20/am.png`;
      else if (code == "ja") return `https://flagcdn.com/w20/jp.png`;
      return `https://flagcdn.com/w20/${code}.png`;
    },
  },
};
</script>

<template>
  <ul>
    <li>title: {{ film.title }}</li>
    <li>original title: {{ film.original_title }}</li>
    <li>
      <img :src="getFlag(film.original_language)" />
    </li>
    <li>vote avg: {{ film.vote_average }}</li>
  </ul>
</template>

<style lang="scss" scoped></style>

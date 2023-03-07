<script>
export default {
  data() {
    return {};
  },

  props: {
    title: String,
    originalTitle: String,
    lang: String,
    vote: Number,
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
    <li>title: {{ title }}</li>
    <li>original title: {{ originalTitle }}</li>
    <li>
      <img :src="getFlag(lang)" />
    </li>
    <li>vote avg: {{ vote }}</li>
  </ul>
</template>

<style lang="scss" scoped></style>

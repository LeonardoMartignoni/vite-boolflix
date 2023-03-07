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
    poster: String,
  },

  methods: {
    getFlag(code) {
      if (code == "en") return `https://flagcdn.com/w20/gb.png`;
      else if (code == "hy") return `https://flagcdn.com/w20/am.png`;
      else if (code == "ja") return `https://flagcdn.com/w20/jp.png`;
      return `https://flagcdn.com/w20/${code}.png`;
    },

    getPoster(image) {
      if (image == null) {
        return `https://images.pexels.com/videos/3045163/free-video-3045163.jpg?auto=compress&cs=tinysrgb&dpr=1&w=500`;
      }
      return `https://image.tmdb.org/t/p/original${image}`;
    },
  },
};
</script>

<template>
  <ul class="ps-0">
    <img
      class="poster"
      :src="getPoster(poster)"
    />
    <li>title: {{ title }}</li>
    <li>original title: {{ originalTitle }}</li>
    <li>
      <img :src="getFlag(lang)" />
    </li>
    <li>vote avg: {{ vote }}</li>
  </ul>
</template>

<style lang="scss" scoped>
ul {
  position: relative;
  width: 280px;
  height: 420px;
  list-style: none;
  .poster {
    width: 100%;
    height: 100%;
    object-fit: cover;
    position: absolute;
    z-index: -1;
  }
}
</style>

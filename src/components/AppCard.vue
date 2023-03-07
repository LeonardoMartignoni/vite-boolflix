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
        return `img-not-found.jpg`;
      }
      return `https://image.tmdb.org/t/p/original${image}`;
    },
  },
};
</script>

<template>
  <div class="card_content ps-0">
    <img
      class="poster"
      :src="getPoster(poster)"
    />
    <div class="card_infos mt-auto p-3">
      <span
        ><span class="card_heading fw-bold d-inline-block">Title: </span>
        {{ title }}</span
      >
      <span
        ><span class="card_heading fw-bold d-inline-block"
          >Original title:
        </span>
        {{ originalTitle }}</span
      >
      <span>
        <img :src="getFlag(lang)" />
      </span>
      <span
        ><span class="card_heading fw-bold d-inline-block">Vote: </span>
        {{ Math.ceil(vote / 2) }}</span
      >
      <!-- <font-awesome-icon icon="fa-solid fa-star" />
      <font-awesome-icon icon="fa-regular fa-star" /> -->
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card_content {
  position: relative;
  width: 280px;
  height: 420px;
  .poster {
    width: 100%;
    height: 100%;
    object-fit: cover;
    position: absolute;
    z-index: -1;
  }
  .card_infos {
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: end;
    background-image: linear-gradient(to top, black, transparent);
    opacity: 0;
    transition: 0.3s;
    &:hover {
      opacity: 1;
    }
    span {
      display: block;
    }
  }
}
</style>

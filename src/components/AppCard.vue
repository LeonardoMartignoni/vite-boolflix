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
      else if (code == "ko") return `https://flagcdn.com/w20/kr.png`;
      else if (code == "zh") return `https://flagcdn.com/w20/cn.png`;
      else if (code == "hi") return `https://flagcdn.com/w20/in.png`;
      else if (code == "el") return `https://flagcdn.com/w20/gr.png`;
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
      <span>
        <span
          class="stars"
          v-for="n in Math.ceil(vote / 2)"
          ><font-awesome-icon icon="fa-solid fa-star"
        /></span>

        <span
          class="stars"
          v-for="n in Math.floor(5 - vote / 2)"
          ><font-awesome-icon icon="fa-regular fa-star"
        /></span>
      </span>
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
    .stars {
      display: inline-block;
      color: gold;
    }
  }
}
</style>

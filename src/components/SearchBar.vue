<script>
export default {
  data() {
    return {
      term: "",
    };
  },

  methods: {
    sendTerm() {
      this.$emit("fetch-results", this.term);
      this.term = "";
    },
  },
};
</script>

<template>
  <div class="navbar_container">
    <nav class="navbar">
      <div class="container-fluid">
        <a
          class="navbar-brand text-uppercase fw-bold fs-2"
          href="#"
          >Boolflix</a
        >
        <div class="d-flex">
          <input
            class="form-control me-2"
            placeholder="Search films or tv series"
            v-model="term"
            @keyup.enter="sendTerm"
          />
          <button
            class="btn btn-outline-danger"
            type="button"
            @click="sendTerm"
          >
            Search
          </button>
        </div>
      </div>
    </nav>
  </div>
</template>

<style lang="scss" scoped>
.navbar_container {
  background-color: #141414;
  position: fixed;
  width: 100%;
  z-index: 1;
}
.navbar-brand {
  color: red;
}
</style>

<script>
export default {
  data() {
    return {
      term: "",
    };
  },
};
</script>

<template>
  <nav class="navbar bg-body-tertiary">
    <div class="container-fluid">
      <a class="navbar-brand">Boolflix</a>
      <form
        class="d-flex"
        role="search"
      >
        <input
          class="form-control me-2"
          type="search"
          placeholder="Search"
          aria-label="Search"
          v-model="term"
        />
        <button
          class="btn btn-outline-success"
          type="button"
          @click="$emit('fetch-results', term)"
        >
          Search
        </button>
      </form>
    </div>
  </nav>
</template>

<style lang="scss" scoped></style>

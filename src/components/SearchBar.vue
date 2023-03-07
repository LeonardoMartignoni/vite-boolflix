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
      <div class="d-flex">
        <input
          class="form-control me-2"
          placeholder="Search"
          v-model="term"
          @keyup.enter="$emit('fetch-results', term)"
        />
        <button
          class="btn btn-outline-success"
          type="button"
          @click="$emit('fetch-results', term)"
        >
          Search
        </button>
      </div>
    </div>
  </nav>
</template>

<style lang="scss" scoped></style>

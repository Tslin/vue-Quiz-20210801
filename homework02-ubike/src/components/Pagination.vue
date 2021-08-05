<template>
  <nav v-if="end > 0">
    <ul class="pagination">
      <li @click.prevent="setPager(cur - 1)" class="page-item">
        <a class="page-link" href>Previous</a>
      </li>

      <li
        v-for="i in end"
        :class="{ active: i + add === cur }"
        :key="i"
        @click.prevent="setPager(i + add)"
        class="page-item"
      >
        <a class="page-link" href>{{ i + add }}</a>
      </li>

      <li @click.prevent="setPager(cur + 1)" class="page-item">
        <a class="page-link" href>Next</a>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  props: ["end", "add", "cur"],
  methods: {
    setPager(value) {
      this.$emit("setPager", value);
    },
  },
};
</script>

<style></style>

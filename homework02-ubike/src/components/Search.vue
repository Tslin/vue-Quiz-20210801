<template>
  <p>
    站點名稱搜尋: <input type="text" v-model="searchText" @input="updateText" />
  </p>
</template>

<script>
export default {
  data() {
    return {
      searchText: "",
    };
  },
  methods: {
    updateText: function() {
      this.$emit("updateText", this.searchText);
    },
  },
};
</script>

<style></style>

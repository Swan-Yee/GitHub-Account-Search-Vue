<template>
  <div
    class="flex justify-between items-center bg-content-white px-2.5 py-1.5 rounded-lg shadow-md mb-6 dark:bg-content-dark"
  >
    <img src="../assets/icon-search.svg" alt="img" class="mr-5" />
    <input
      type="text"
      name=""
      placeholder="Search Github Name....."
      class="w-100 grow focus:outline-none placeholder-size dark:bg-content-dark dark:caret-white dark:text-white"
      autocomplete="off"
      v-model="inputData"
      @keyup.enter="search"
    />
    <button
      class="bg-btn-primary text-text-dark p-3 rounded-xl w-24 text-md tracking-wider hover:bg-btn-hover"
      @click="search"
    >
      Search
    </button>
  </div>
</template>

<script>
export default {
  name: "SearchInput",
  data() {
    return {
      inputData: "",
    };
  },
  methods: {
    search() {
      this.$emit("search-data", this.inputData);
    },
  },
};
</script>

<style></style>

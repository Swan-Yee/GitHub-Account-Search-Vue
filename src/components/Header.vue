<template>
  <header class="header flex justify-between items-center mb-8">
    <h1 class="text-lg font-bold text-text-white dark:text-white">devfinder</h1>
    <a href="#" class="flex" @click="toggleDarkMode">
      <p class="mr-5 font-bold text-text-white dark:text-white tracking-widest">
        DARK
      </p>
      <div class="icon">
        <img
          src="../assets/icon-moon.svg"
          alt="img"
          class="block dark:hidden"
        />
        <img src="../assets/icon-sun.svg" alt="img" class="hidden dark:block" />
      </div>
    </a>
  </header>
</template>

<script>
export default {
  name: "HeaderNav",
  methods: {
    toggleDarkMode() {
      this.$emit("toggleDarkMode");
    },
  },
};
</script>

<style></style>

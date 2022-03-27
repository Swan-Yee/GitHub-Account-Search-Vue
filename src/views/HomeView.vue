<template>
  <div :class="darkMode ? 'dark' : ''">
    <div
      class="bg-white min-w-screen min-h-screen font-space-mono text-base dark:bg-dark"
    >
      <div class="py-5 mx-auto w-5/6 md:w-2/3 lg:w-2/5">
        <!-- header Component -->
        <header-nav @toggleDarkMode="toggleDarkMode"></header-nav>
        <!-- Main Content -->
        <main>
          <search-input @search-data="fetchData"></search-input>
          <user-list :data="fetchedData"></user-list>
        </main>
      </div>
    </div>
  </div>
</template>

<script>
import HeaderNav from "@/components/Header.vue";
import SearchInput from "@/components/SearchInput.vue";
import UserList from "@/components/UserList.vue";

export default {
  name: "HomeView",
  data() {
    let darkMode = localStorage.getItem("darkMode") == "true";
    return {
      fetchedData: {},
      darkMode,
    };
  },
  components: {
    "header-nav": HeaderNav,
    "search-input": SearchInput,
    "user-list": UserList,
  },
  methods: {
    async fetchData(name) {
      const res = await fetch(`https://api.github.com/users/${name}`);
      const data = await res.json();
      this.fetchedData = data;
    },
    toggleDarkMode() {
      this.darkMode = !this.darkMode;
      localStorage.setItem("darkMode", this.darkMode);
    },
  },
  async created() {
    await this.fetchData("octocat");
  },
};
</script>

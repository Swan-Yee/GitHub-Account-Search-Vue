<template>
  <div
    class="bg-content-white rounded-lg shadow-lg dark:bg-content-dark dark:text-white"
  >
    <div class="p-5 md:p-10">
      <div class="flex flex-row items-center">
        <img
          :src="data.avatar_url"
          alt="img"
          class="rounded-full w-1/3 mr-10"
          id="image"
        />
        <div class="about">
          <p class="text-xl font-bold" id="name">
            {{ data.name }}
          </p>
          <a
            :href="data.html_url"
            class="text-btn-primary dark:text-white"
            id="userName"
          >
            @{{ data.login }}
          </a>
          <p class="text-muted font-bold dark:text-white">
            {{ date(data.created_at) }}
          </p>
        </div>
      </div>
      <div>
        <p class="text-muted my-8 dark:text-white" id="bio" v-if="data.bio">
          {{ data.bio }}
        </p>
        <p class="text-muted my-8 dark:text-white" id="bio" v-else>
          No Bio to show
        </p>
      </div>
      <div
        class="bg-white flex justify-between items-center p-5 rounded-lg shadow-sm dark:bg-dark"
      >
        <div>
          <p class="text-muted dark:text-white">Repos</p>
          <p class="font-bold text-lg">{{ data.public_repos }}</p>
        </div>
        <div>
          <p class="text-muted dark:text-white">Followers</p>
          <p class="font-bold text-lg" id="followers">{{ data.followers }}</p>
        </div>
        <div>
          <p class="text-muted dark:text-white">Following</p>
          <p class="font-bold text-lg" id="following">{{ data.following }}</p>
        </div>
      </div>
      <div class="grid gap-4 grid-cols-2 gap-x-8 mt-5">
        <div class="flex">
          <img
            src="../assets/icon-location.svg"
            alt="img"
            class="inline mr-5"
          />
          <p
            class="text-muted dark:text-white {{ data.location ? '' : 'opacity-50' }}"
          >
            {{ data.location ? data.location : "Not Avaliable" }}
          </p>
        </div>
        <div class="flex">
          <img src="../assets/icon-twitter.svg" alt="img" class="inline mr-5" />
          <p
            class="text-muted dark:text-white {{ data.twitter_username ? '' : 'opacity-50' }}"
          >
            {{
              data.twitter_username ? data.twitter_username : "Not Avaliable"
            }}
          </p>
        </div>
        <div class="flex">
          <img src="../assets/icon-website.svg" alt="img" class="inline mr-5" />
          <p
            class="text-muted dark:text-white {{ data.blog ? '' : 'opacity-50' }}"
          >
            {{ data.blog ? data.blog : "Not Avaliable" }}
          </p>
        </div>
        <div class="flex">
          <img src="../assets/icon-company.svg" alt="img" class="inline mr-5" />
          <p
            class="text-muted dark:text-white {{ data.company ? '' : 'opacity-50' }}"
          >
            {{ data.company ? data.company : "Not Avaliable" }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import moment from "moment";
export default {
  name: "UserList",
  props: {
    data: {
      require: true,
      type: Object,
    },
  },
  methods: {
    moment: function (date) {
      return moment(date);
    },
    date: function (date) {
      return moment(date).format("MMMM Do YYYY");
    },
  },
};
</script>

<style></style>

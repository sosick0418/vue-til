<template>
  <div>
    <div class="main list-container contents">
      <h1 class="page-header">Today I Learned</h1>
      <ul>
        <li v-for="postItem in postItems" :key="postItem._id">
          {{ postItem.title }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import { fetchPosts } from '@/api/index';
export default {
  data() {
    return {
      postItems: [],
    };
  },
  methods: {
    async fetchData() {
      try {
        const { data } = await fetchPosts();
        this.postItems = data.posts;
      } catch (error) {
        console.log(error);
      }
    },
  },
  created() {
    this.fetchData();
  },
};
</script>

<style></style>

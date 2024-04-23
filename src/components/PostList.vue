<template>
    <div>
      <h3>Post Lists</h3>
      <button @click="getPosts">Load Posts</button>
      <ul>
        <li v-for="post in posts" :key="post.id">
          {{ post.title }}
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    name: 'PostList',
    data() {
      return {
        posts: [],
      };
    },
    methods: {
      getPosts() {
        axios.get('https://jsonplaceholder.typicode.com/posts')
          .then((response) => {
            this.posts = response.data; // Assign the response data to the posts array
          })
          .catch((error) => {
            console.error('Error loading the posts:', error);
            // Optionally handle error in UI, e.g., a data property for errors displayed in template
          });
      }
    },
    mounted() {
      // Optionally auto-load posts when component mounts
      this.getPosts();
    }
  }
  </script>
  
  <style scoped>
  </style>
  
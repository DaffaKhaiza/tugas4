<template>
    <div>
      <h2>Posts for {{ userName }}</h2>
      <ul>
        <PostItem
          v-for="post in posts"
          :key="post.id"
          :post="post"
          @show-detail="showDetail"
        />
      </ul>
    </div>
</template>
  
<script>
  import axios from 'axios';
  import PostItem from './PostItem.vue';
  
  export default {
    components: {
      PostItem,
    },
    props: {
      userId: Number,
      userName: String,
    },
    data() {
      return {
        posts: [],
      };
    },
    watch: {
      userId: {
        immediate: true,
        handler(newVal) {
          if (newVal) {
            this.fetchPosts(newVal);
          }
        },
      },
    },
    methods: {
      async fetchPosts(userId) {
        const response = await axios.get(`https://jsonplaceholder.typicode.com/posts?userId=${userId}`);
        this.posts = response.data;
      },
      showDetail(post) {
        this.$emit('show-detail', post);
      },
    },
  };
</script>
  
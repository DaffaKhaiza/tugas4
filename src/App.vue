<template>
  <div id="app">
    <h1>POST</h1>
    <UserList @user-selected="displayUserPosts" />
    <PostList v-if="selectedUser" :userId="selectedUser.id" :userName="selectedUser.name" @show-detail="displayPostDetail" />
    <PostDetail :post="selectedPost" />
  </div>
</template>

<script>
import UserList from './components/UserList.vue';
import PostList from './components/PostList.vue';
import PostDetail from './components/PostDetail.vue';

export default {
  components: {
    UserList,
    PostList,
    PostDetail,
  },
  data() {
    return {
      selectedUser: null,
      selectedPost: null,
    };
  },
  methods: {
    displayUserPosts(user) {
      this.selectedUser = user;
      this.selectedPost = null;
    },
    displayPostDetail(post) {
      this.selectedPost = post;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 20px;
}
</style>

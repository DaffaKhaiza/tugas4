<template>
    <div>
      <h2>Select a User</h2>
      <button @click="fetchUsers" v-if="!users.length">Load Users</button>
      <ul>
        <li v-for="user in users" :key="user.id" @click="selectUser(user)">
          {{ user.name }}
        </li>
      </ul>
    </div>
</template>
  
<script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        users: [],
      };
    },
    methods: {
      async fetchUsers() {
        const response = await axios.get('https://jsonplaceholder.typicode.com/users');
        this.users = response.data;
      },
      selectUser(user) {
        this.$emit('user-selected', user);
      },
    },
  };
</script>
  
<style scoped>
  li {
    cursor: pointer;
    margin-bottom: 10px;
  }
  li:hover {
    color: blue;
  }
</style>
  
<style scoped>
  div {
    margin-top: 20px;
  }

  h2 {
    color: #333;
    font-size: 1.8rem;
    margin-bottom: 10px;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }
</style>

<style scoped>
  div {
    margin-top: 20px;
  }

  h2 {
    color: #f4f4f4;
    font-size: 1.8rem;
    margin-bottom: 10px;
  }

  button {
    padding: 10px 20px;
    font-size: 1rem;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  button:hover {
    background-color: #0056b3;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    cursor: pointer;
    margin-bottom: 10px;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 10px;
    background-color: #f9f9f9;
    transition: all 0.3s ease;
  }

  li:hover {
    color: rgb(255, 0, 217);
    transform: translateY(-5px);
    box-shadow: 0px 0px 20px 0px rgba(234, 229, 229, 0.1);
  }
</style>
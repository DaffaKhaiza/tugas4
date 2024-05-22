<template>
    <li>
      <div @click="toggleDetail">
        {{ post.title }}
      </div>
      <div v-if="showingDetail">
        <p>{{ post.body }}</p>
      </div>
    </li>
</template>
  
<script>
  export default {
    props: ['post'],
    data() {
      return {
        showingDetail: false,
      };
    },
    methods: {
      toggleDetail() {
        this.showingDetail = !this.showingDetail;
        if (this.showingDetail) {
          this.$emit('show-detail', this.post);
        }
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
    color: blue;
    transform: translateY(-5px);
    box-shadow: 0px 0px 20px 0px rgba(0, 0, 0, 0.1);
  }

  div {
    color: #333;
    font-size: 1rem;
    margin-bottom: 5px;
  }

  p {
    color: #666;
    font-size: 0.9rem;
  }
</style>
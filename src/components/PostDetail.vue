<template>
    <div v-if="post">
      <h3>{{ post.title }}</h3>
      <p>{{ post.body }}</p>
    </div>
</template>
  
<script>
  export default {
    props: ['post'],
  };
</script>
  
<style scoped>
  div {
    margin-top: 20px;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 10px;
    background-color: #f9f9f9;
    box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.1);
  }

  h3 {
    color: #333;
    font-size: 1.5rem;
    margin-bottom: 10px;
  }

  p {
    color: #666;
    font-size: 1rem;
  }
</style>
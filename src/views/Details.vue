<template>
    <div class="details-page">
      <h1 class="page-title">Details Page</h1>
  
      <!-- Error Message -->
      <div v-if="error" class="error-message">
        {{ error }}
      </div>
  
      <!-- Post Content -->
      <div v-if="post" class="post-content">
        <h2 class="post-title">{{ post.title }}</h2>
        <p class="post-body">{{ post.body }}</p>
  
        <div class="post-tags">
          <span class="tag" v-for="tag in post.tags" :key="tag">
            #{{ tag }}
          </span>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import getPost from '../composables/getPost'
  
  export default {
    props: ['id'],
    setup(props) {
      const { post, error, load } = getPost(props.id);
      load();
      return { error, post };
    }
  }
  </script>
  
  <style scoped>
  /* General page styles */
  .details-page {
    padding: 20px;
    max-width: 800px;
    margin: 0 auto;
    background-color: #f9f9f9; /* Light gray background for the whole page */
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }
  
  .page-title {
    font-size: 2rem;
    text-align: center;
    margin-bottom: 20px;
    color: #333; /* Darker text color for better readability */
  }
  
  /* Error message styles */
  .error-message {
    background-color: #ffdddd;
    color: #d8000c;
    padding: 15px;
    border-radius: 8px;
    border: 1px solid #f5c6cb;
    text-align: center;
    margin-bottom: 20px;
    font-weight: bold;
  }
  
  /* Post content styles */
  .post-content {
    background-color: #ffffff; /* White background for the post */
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }
  
  .post-title {
    font-size: 1.8rem;
    font-weight: bold;
    color: #007bff; /* Blue color for the title */
    margin-bottom: 15px;
  }
  
  .post-title:hover {
    color: #0056b3; /* Darker blue on hover */
  }
  
  .post-body {
    font-size: 1rem;
    line-height: 1.6;
    color: #555; /* Softer gray for body text */
    margin-bottom: 20px;
  }
  
  /* Tag styles */
  .post-tags {
    display: flex;
    flex-wrap: wrap; /* Wrap tags onto a new line if they don't fit */
    gap: 10px; /* Space between tags */
  }
  
  .tag {
    background-color: #007bff;
    color: #ffffff;
    font-size: 0.875rem;
    padding: 5px 12px;
    border-radius: 20px;
    transition: background-color 0.3s;
  }
  
  .tag:hover {
    background-color: #0056b3; /* Slightly darker blue on hover */
  }
  </style>
  
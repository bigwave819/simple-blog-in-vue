<template>
    <div class="post">
      <router-link :to="{ name: 'Details', params: { id: post.id }}" class="post-title">
        <h2>{{ post.title }}</h2>
      </router-link>
      <p class="post-snippet">{{ snippets }}</p>
      <div class="post-tags">
        <span class="tag" v-for="tag in post.tags" :key="tag">
          #{{ tag }}
        </span>
      </div>
    </div>
  </template>
  
  <script>
  import { computed } from 'vue';
  
  export default {
    props: ['post'],
    setup(props) {
      const snippets = computed(() => {
        return props.post.body.substring(0, 100) + '...';
      });
  
      return { snippets };
    }
  }
  </script>
  
  <style scoped>
  /* Main container for a single post */
  .post {
    background-color: #ffffff; /* White background for each post */
    border-radius: 10px; /* Rounded corners */
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); /* Subtle shadow for elevation */
    padding: 20px; /* Spacing inside the card */
    margin-bottom: 20px; /* Space between posts */
    transition: transform 0.2s, box-shadow 0.2s; /* Smooth hover animation */
  }
  
  .post:hover {
    transform: translateY(-5px); /* Slight lift effect */
    box-shadow: 0 8px 12px rgba(0, 0, 0, 0.15); /* Stronger shadow on hover */
  }
  
  /* Title of the post */
  .post-title {
    text-decoration: none; /* Remove underline from the link */
    color: #333; /* Dark color for better readability */
  }
  
  .post-title h2 {
    font-size: 1.5rem; /* Font size for the post title */
    font-weight: bold; /* Make the title bold */
    margin-bottom: 10px; /* Space between title and snippet */
    transition: color 0.2s; /* Smooth color change on hover */
  }
  
  .post-title:hover h2 {
    color: #007BFF; /* Change color to blue on hover */
  }
  
  /* Snippet / excerpt of the post */
  .post-snippet {
    color: #666; /* Gray text for the post snippet */
    font-size: 1rem; /* Font size for the snippet */
    line-height: 1.6; /* Line height for better readability */
    margin-bottom: 15px; /* Space between snippet and tags */
  }
  
  /* Tags container */
  .post-tags {
    display: flex;
    flex-wrap: wrap; /* Wrap tags to next line if they don't fit */
    gap: 10px; /* Space between tags */
  }
  
  .tag {
    background-color: #007BFF; /* Blue background for tags */
    color: #ffffff; /* White text for contrast */
    font-size: 0.875rem; /* Slightly smaller text for tags */
    padding: 5px 10px; /* Padding for better spacing */
    border-radius: 20px; /* Fully rounded corners for pills */
    transition: background-color 0.2s; /* Smooth color change on hover */
  }
  
  .tag:hover {
    background-color: #0056b3; /* Darker blue on hover */
  }
  </style>
  
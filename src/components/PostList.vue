<template>
  <div class="post-list">
    <div class="post-item" v-for="post in posts" :key="post.id">
      <SinglePost :post="post" />
    </div>
  </div>
</template>

<script>
import SinglePost from './SinglePost.vue';

export default {
  components: { SinglePost },
  props: ['posts'],
}
</script>

<style scoped>
/* Main container for the list of posts */
.post-list {
  display: flex;
  flex-wrap: wrap; /* Allows posts to wrap to the next row */
  gap: 20px; /* Spacing between posts */
  justify-content: center; /* Center align the posts */
  padding: 20px;
  background-color: #f4f4f9; /* Light background for contrast */
  border-radius: 10px;
}

/* Each individual post item */
.post-item {
  width: 300px; /* Controls the width of each post */
  background-color: #ffffff; /* White background for individual posts */
  border-radius: 10px; /* Rounded corners for a modern look */
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); /* Subtle shadow for a lifted effect */
  transition: transform 0.2s, box-shadow 0.2s; /* Smooth animations on hover */
  overflow: hidden; /* To prevent content from overflowing the container */
}

/* Hover effect to make the post "pop" */
.post-item:hover {
  transform: translateY(-10px); /* Lift up the post */
  box-shadow: 0 8px 12px rgba(0, 0, 0, 0.15); /* Stronger shadow on hover */
}

</style>

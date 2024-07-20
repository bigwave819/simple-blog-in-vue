<template>
    <h1>Details Page</h1>
    <div v-if="error">{{ error }}</div>
    <div v-if="post">
        <h2>{{ post.title }}</h2>
        <p>{{ post.body }}</p>
        <span v-for="tag in post.tags" :key="tag">
            #{{ tag }}
        </span>
    </div>
</template>
<script>
import getPost from '../composables/getPost'

export default{
    props: ['id'],
    setup(props){
        const { post, error, load} = getPost(props.id);

        load()

        return{ error, post}
    }
}
</script>
<script setup>
import Navbar from "../components/Navbar.vue";
import BlogPostPreview from "../components/BlogPostPreview.vue";
import CreatePostForm from "../components/CreatePostForm.vue";
import { ref, provide } from "vue";

const posts = ref([]);

provide("posts", posts);

const addPost = (newPost) => {
    posts.value.push(newPost);
}

const deletePost = (postIndex) => {
    posts.value.splice(postIndex, 1)
}

</script>

<template>
<Navbar />


<CreatePostForm @create-post="addPost"/>

<h1 class="container mx-auto px-10 mt-12 text-3xl font-bold">My Blog Posts</h1>


<BlogPostPreview 
v-for="(post, index) in posts"
:key="index"
:post="post"
@delete-post="deletePost(index)"
/>


</template>


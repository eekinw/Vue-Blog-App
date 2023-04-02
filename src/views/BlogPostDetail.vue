<script setup>
import { inject, computed } from "vue";
import { useRoute, RouterLink } from "vue-router"; // to retrieve the id from the route

const route = useRoute();
const postId = parseInt(route.params.id, 10); // this is the id from the route
const posts = inject("posts"); // this is the posts array from the provide in HomePage.vue


const post = computed(() => {
    return posts.value.find((post) => post.id === postId);
});


</script>

<template>
    <div v-if="post">
        <h1>{{ post.title}}</h1>
        <p>{{ post.content }}</p>
        <p class="text-sm italic">{{ post.author }}</p>
        <RouterLink 
        to="/"
        class="text-blue-500 hover:underline"
        >
        Back to Home
        </RouterLink>
    </div>
    <div v-else>
        <p>Post Not Found</p>
    </div>

</template>


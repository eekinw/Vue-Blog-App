<script setup>
import { RouterLink } from 'vue-router';

const props = defineProps({
    post: {
        type: Object,
        required: true
    }
})

const emit = defineEmits(["delete-post"]);

</script>

<template>
    <div class=" bg-yellow-200 mx-10 p-5 rounded-lg mt-8">
        <div class=" bg-slate-100 rounded-lg p-3 space-y-3 mb-5">
            <div class="flex justify-between">
                <h3 class="text-xl font-bold">{{ post.title}}</h3>
                <div class="flex items-center">
                    <RouterLink :to="{
                        name: 'BlogPostDetail',
                        params: { id: post.id } 
                    }"
                    class="ml-5 text-sm text-blue-500 hover:underline mr-3"
                    >See More
                    </RouterLink>
                    <button 
                    class="bg-red-500 text-white px-4 py-2 rounded"
                    @click="$emit('delete-post')"
                    >Delete</button>
                </div>
            </div>
            <p class=""> {{ post.content }}</p>
            <p class="text-sm italic">{{ post.author}}</p>
        </div>
    </div>

</template>


<script setup>
import { ref } from "vue";

// installed a library called uuid to generate unique ids for each post
import { v4 as uuidv4 } from "uuid";


const title = ref("");
const content = ref("");
const author = ref("");
const showForm = ref(false);

const emit = defineEmits(["create-post"]);

const submitForm = () => {
    emit("create-post", {
        id: uuidv4(),
        title: title.value,
        content: content.value,
        author: author.value
    });
    title.value = "";
    content.value = "";
    author.value = "";
    showForm.value = false;
}

const openForm = () => {
    showForm.value = true;
}

</script>

<template>
<!-- Make it like a modal where after button is clicked the form appears -->

<div class="flex justify-center items-center mt-3">
    <button 
    class="p-2 rounded-lg border-2 border-sky-500 w-1/4 hover:scale-105 cursor-pointer"
    @click="openForm"
    >Create a Post</button>
</div>


<div
    v-if="showForm"
    class="fixed inset-0 bg-black bg-opacity-60 flex items-center justify-center"
  >
  <!-- fixed inset-0 works together to create a full screen overlay -->
<form class="p-5" @submit.prevent="submitForm">
    <div class="mb-5">
        <label for="title">Title: </label>
        <input 
        id="title"
        type="text"
        class="border-2 border-gray-300 p-2 rounded-lg w-full"
        v-model="title"
        required
        />
    </div>

    <div class="mb-5">
        <label for="content">Content</label>
        <textarea 
        name="content" 
        id="content" 
        cols="30" 
        rows="10"
        class="border-2 border-gray-300 p-2 rounded-lg w-full"
        v-model="content"
        required
        ></textarea>
    </div>

    <div class="mb-5">
        <label for="author">Author: </label>
        <input 
        type="text"
        class="border-2 border-gray-300 p-2 rounded-lg w-full"
        v-model="author"
        required
        />
    </div>

    <button type="submit" class="bg-blue-500 text-white px-4 py-2 rounded">Submit</button>
    <button 
    type="button" 
    class="bg-red-500 text-white px-4 py-2 rounded ml-3"
    @click="showForm = false"
    >Cancel</button>
</form>
</div>
</template>
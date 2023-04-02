<script setup>
import {useRouter} from "vue-router"

const router = useRouter()

</script>

<template>
    <div class="flex flex-col justify-center items-center min-h-screen">
        <h1 class=" text-5xl">404 - Page Not Found</h1>
        <button @click="router.back()" class="mt-20 p-2 rounded-lg border-2 border-rose-500">Go Back</button>
    </div> 

</template>
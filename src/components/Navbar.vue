<script setup>
import { RouterLink } from 'vue-router';



</script>

<template>
    <nav class="bg-gray-800 py-4">
      <div class="container mx-auto flex justify-between items-center px-10">
        <div class="text-white font-bold">
          <!-- Add your logo or application name here -->
          <h1>My Blog</h1>
        </div>
        <div class="text-white">
          <!-- Add your navigation links here -->
          <RouterLink class="ml-4" to="/">Home</RouterLink>
          <RouterLink class="ml-4" to="/about">About</RouterLink>
        </div>
      </div>
    </nav>
  </template>
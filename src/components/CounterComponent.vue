<template>
    <div class="counter">
      <p>Count: {{ count }}</p>
      <button @click="increment">Increment</button>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const count = ref(0)
  
  const increment = () => {
    count.value++
  }
  </script>
  
  <style>
  .counter {
    padding: 20px;
    border: 1px solid #ccc;
    margin: 10px;
  }
  </style>
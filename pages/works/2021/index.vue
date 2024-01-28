<script setup>
const { data: works } = await useFetch("http://localhost:3000/api/works");
const { data: authors } = await useFetch("http://localhost:3000/api/authors");
</script>

<template>
  <h1>点の展2021 at oneline</h1>
  <div v-for="work in works" :key="work.id">
    <p>タイトル：{{ work.title }}</p>
    {{ work.description }}
  </div>
</template>

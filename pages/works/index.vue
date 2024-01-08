<script setup>
const { data, pending, error, refresh } = await useFetch('http://localhost:3000/api/works')
console.log(data)
</script>


<template>
  <div>
        {{ data }}
  </div>
</template>
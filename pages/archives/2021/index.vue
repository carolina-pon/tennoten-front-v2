<script setup>
const { data: works } = await useFetch("http://localhost:3000/api/works");
const { data: authors } = await useFetch("http://localhost:3000/api/authors");

const getAuthorName = (authorId) => {
  const author = authors.value.find((author) => author.id === authorId);
  return author ? author.name : "";
};
</script>

<template>
  <p class="text-h5 text-center">点の展 2021 AT ONELINE</p>
  <v-container>
    <v-row>
      <v-col cols="12" md="4" v-for="work in works" :key="work.id">
        <router-link
          :to="`/archives/2021/${work.id}`"
          style="text-decoration: none; color: inherit"
        >
        <v-card class="mx-auto" max-width="350px">
          <v-img
            height="200px"
            src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
            cover
          ></v-img>

          <v-card-title>{{ work.title }}</v-card-title>
          <v-card-text>{{ getAuthorName(work.author_id) }}</v-card-text>
        </v-card>
        </router-link>
      </v-col>
    </v-row>
  </v-container>
</template>

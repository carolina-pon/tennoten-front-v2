<script setup>
const route = useRoute();
const { data: work } = await useFetch(
  `http://localhost:3000/api/works/${route.params.id}`
);
const { data: authors } = await useFetch(`http://localhost:3000/api/authors/`);
const getAuthorName = (authorId) => {
  const author = authors.value.find((author) => author.id === authorId);
  return author ? author.name : "";
};
</script>
<template>
  <v-container>
    <v-row justify="center">
      <v-col cols="8" md="8">
        <v-card class="mx-auto" flat>
          <v-img
            max-height="600px"
            src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
            cover
          ></v-img>
          <v-divider :thickness="30" color="white"></v-divider>
          <v-card-title
            ><span>『</span>{{ work.title }}<span>』</span></v-card-title
          >
          <v-card-text class="text-right">{{
            getAuthorName(work.author_id)
          }}</v-card-text>
          <v-card-subtitle>{{ work.description }}</v-card-subtitle>
          <v-card-subtitle class="text-right"
            >作品ジャンル：{{ work.material }}</v-card-subtitle
          >
          <v-card-subtitle class="text-right"
            >サイズ：{{ work.size }}</v-card-subtitle
          >
          <v-card-subtitle class="text-right"
            >重さ：{{ work.weight }}</v-card-subtitle
          >
          <v-divider :thickness="30" color="white"></v-divider>
          <v-divider color="black"></v-divider>
        </v-card>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="8">
        <v-btn icon to="/archives/2021/" nuxt><v-icon>mdi-arrow-left</v-icon></v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

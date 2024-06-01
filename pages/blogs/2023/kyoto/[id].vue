<script setup>
const route = useRoute();
const { data: blog } = await useFetch(
  `http://localhost:3000/api/blogs/${route.params.id}`
);
const { data: authors } = await useFetch(
  `http://localhost:3000/api/authors/`
);
const getAuthorName = (authorId) => {
  const author = authors.value.find((author) => author.id === authorId);
  return author ? author.name : "";
};
</script>

<template>
  <v-container>
    <v-row justify="center">
      <v-col cols="10">
        <v-avatar class="ma-3" size="50" rounded="5" color="surface-variant">
        </v-avatar>
        <span class="text-h5">{{ getAuthorName(blog.author_id) }}</span>
        <v-divider color="black"></v-divider>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="10">
        <body>
          {{ blog.description }}
        </body>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="10">
        <v-divider color="black"></v-divider>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="10">
        <v-btn icon to="/blogs/2023/kyoto" nuxt><v-icon>mdi-arrow-left</v-icon></v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

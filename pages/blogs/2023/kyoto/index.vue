<script setup>
const { data: authors } = await useFetch("http://localhost:3000/api/authors");
const { data: blogs } = await useFetch("http://localhost:3000/api/blogs");

const getAuthorName = (authorId) => {
  const author = authors.value.find((author) => author.id === authorId);
  return author ? author.name : "";
};
</script>

<template>
  <p class="text-h5 text-center">
    INNTERVIEW BLOG 2023<v-icon icon="mdi-fountain-pen"></v-icon> IN KYOTO
  </p>
  <v-container>
    <v-row>
      <v-col cols="12" md="4" v-for="blog in blogs" :key="blog.id">
        <v-card>
          <v-card-item>
            <div class="d-flex justify-center">
              <v-avatar size="250">
                <v-img src="https://cdn.vuetifyjs.com/images/john.jpg"></v-img>
              </v-avatar>
            </div>
            <v-divider :thickness="9" color="white"></v-divider>
            <p class="text-h5 d-flex justify-center">{{ getAuthorName(blog.author_id) }}</p>
          </v-card-item>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

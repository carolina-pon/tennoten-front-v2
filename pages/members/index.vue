<script setup>
const { data: authors } = await useFetch("http://localhost:3000/api/authors");
</script>

<template>
  <p class="text-h5 text-center">MEMBERS</p>
  <v-container>
    <v-row>
      <v-col cols="4" md="4" v-for="author in authors" :key="author.id">
        <v-card>
          <v-card-item>
            <div class="d-flex justify-center">
              <v-avatar size="250">
                <v-img src="https://cdn.vuetifyjs.com/images/john.jpg"></v-img>
              </v-avatar>
            </div>
            <v-divider :thickness="9" color="white"></v-divider>
            <p class="text-h5 d-flex justify-center">{{ author.name }}</p>
          </v-card-item>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

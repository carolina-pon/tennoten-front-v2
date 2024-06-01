<script setup>
const route = useRoute();
const { data: author } = await useFetch(
  `http://localhost:3000/api/authors/${route.params.id}`
);
</script>

<template>
  <v-container>
    <v-row justify="center">
      <v-col cols="12" md="4">
        <div class="d-flex justify-center">
          <v-avatar size="350">
            <v-img src="https://cdn.vuetifyjs.com/images/john.jpg"></v-img>
          </v-avatar>
        </div>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="12" md="4">
        <v-divider color="black"></v-divider>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="12" md="4">
        <p class="text-h5 d-flex justify-center">
          <span>名前：{{ author.name }}</span>
        </p>
        <p class="text-h5 d-flex justify-center">
          <span>活動拠点：{{ author.site }}</span>
        </p>
        <p class="text-h5 d-flex justify-center">
          <span>SNS：{{ author.sns }}</span>
        </p>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="12" md="4">
        <v-divider color="black"></v-divider>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="10">
        <v-btn icon to="/members" nuxt><v-icon>mdi-arrow-left</v-icon></v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<template>
  <v-container>
  <v-layout class="rounded rounded-md">
    <v-app-bar flat>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
      <v-app-bar-title>点の展</v-app-bar-title>
      <v-btn icon href="https://twitter.com/tennoten_">
        <v-icon>mdi-twitter</v-icon>
      </v-btn>
      <v-btn icon href="https://www.instagram.com/tennoten_/">
        <v-icon>mdi-instagram</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <v-img src="~/assets/main.png" max-width="100%"> </v-img>
    </v-main>
  </v-layout>
  <v-footer>
    <v-col class="text-center mt-4" cols="12"
      >©︎2024 <strong>点の展</strong>
    </v-col>
  </v-footer>
</v-container>
</template>

<script setup></script>

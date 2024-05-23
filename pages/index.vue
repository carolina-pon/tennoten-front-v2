<template>
  <v-container>
  <v-layout class="rounded rounded-md">
    <v-app-bar flat>
      <v-menu
      transition="slide-y-transition"
    >
      <template v-slot:activator="{ props }">
        <v-btn icon
          v-bind="props"
        ><v-icon>mdi-dots-horizontal</v-icon>
        </v-btn>
      </template>
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
        >
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-menu>

      <v-app-bar-title>点の展</v-app-bar-title>
      <v-btn>ABOUT</v-btn>
      <v-btn>MEMBERS</v-btn>
      <v-btn>INTERVIEW BLOG</v-btn>
      <v-btn>ARCHIVES</v-btn>
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

<script setup>
  const items=  [
        { title: 'ABOUT' },
        { title: 'MEMBERS' },
        { title: 'INTERVIEW BLOG' },
        { title: 'ARCHIVES' },
      ]
</script>
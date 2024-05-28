<template>
  <v-container>
    <v-layout class="rounded rounded-md">
      <v-app-bar flat>
        <v-menu transition="slide-y-transition">
          <template v-slot:activator="{ props }">
            <v-btn icon v-bind="props"
              ><v-icon>mdi-dots-horizontal</v-icon>
            </v-btn>
          </template>
          <v-list>
            <v-list-item v-for="(item, i) in items" :key="i">
              <router-link
                :to="item.link"
                style="text-decoration: none; color: inherit"
              >
                <v-list-item-title>{{ item.title }}</v-list-item-title>
              </router-link>
            </v-list-item>
          </v-list>
        </v-menu>

        <v-app-bar-title>点の展</v-app-bar-title>
        <v-btn to="/about" nuxt>ABOUT</v-btn>
        <v-btn to="/members" nuxt>MEMBERS</v-btn>
        <v-btn to="/blogs/2023/kyoto" nuxt>INTERVIEW BLOG</v-btn>
        <v-btn to="/archives/2021" nuxt>ARCHIVES</v-btn>
        <v-btn icon href="https://twitter.com/tennoten_">
          <v-icon>mdi-twitter</v-icon>
        </v-btn>
        <v-btn icon href="https://www.instagram.com/tennoten_/">
          <v-icon>mdi-instagram</v-icon>
        </v-btn>
      </v-app-bar>
    </v-layout>
  </v-container>
</template>

<script setup>
const items = [
  { title: "ABOUT", link: "/about" },
  { title: "MEMBERS", link: "/members" },
  { title: "INTERVIEW BLOG", link: "/blogs/2023/kyoto" },
  { title: "ARCHIVES", link: "/archives/2021" },
];
</script>

<!-- <template>
  <v-app-bar>
    <template v-slot:prepend>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
    </template>
    <v-app-bar-title>点の展</v-app-bar-title>
  </v-app-bar>
</template> -->

<template>
  <v-layout class="rounded rounded-md">
    <v-app-bar>
      <v-app-bar-title>点の展</v-app-bar-title>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
    </v-app-bar>

    <v-navigation-drawer>
      <v-list>
        <v-list-item title="Navigation drawer"> </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main
      class="d-flex align-center justify-center"
      style="min-height: 300px"
    >
      Main Content
      <Timeline
        id="twitterdev"
        sourceType="profile"
        :options="{ tweetLimit: '3' }"
      />
    </v-main>
  </v-layout>
  <v-footer>
    <v-col class="text-center mt-4" cols="12"
      >2024 <strong>点の展</strong>
    </v-col>
  </v-footer>
</template>

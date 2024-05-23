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
          <v-card-title><span>『</span>夜空の星<span>』</span></v-card-title>
          <v-card-text class="text-right">永田　里奈</v-card-text>
          <v-card-subtitle class="text-right"
            >作品ジャンル：写真</v-card-subtitle
          >
          <v-card-subtitle>これは夜空の撮影をしました。</v-card-subtitle>
          <v-divider :thickness="30" color="white"></v-divider>
          <v-divider color="black"></v-divider>
        </v-card>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="8">
        <v-btn icon><v-icon>mdi-arrow-left</v-icon></v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

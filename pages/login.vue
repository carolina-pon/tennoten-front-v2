<script setup></script>

<template>
  <div class="bg-grey-lighten-3 pt-10 pb-10">
    <p class="text-h5 text-center">管理者ログインページ</p>
    <v-container>
      <div>
        <v-card class="mx-auto pa-12 pb-8" max-width="448" rounded="lg" flat>

          <v-text-field
            density="compact"
            placeholder="Email address"
            prepend-inner-icon="mdi-email-outline"
            variant="outlined"
          ></v-text-field>

          <v-text-field
            :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
            :type="visible ? 'text' : 'password'"
            density="compact"
            placeholder="Password"
            prepend-inner-icon="mdi-lock-outline"
            variant="outlined"
            @click:append-inner="visible = !visible"
          ></v-text-field>
          <v-btn class="mb-8" size="large" variant="tonal" block>
            LOG IN
          </v-btn>
        </v-card>
      </div>
    </v-container>
  </div>
</template>

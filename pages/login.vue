<script setup>
// const { signIn } = useAuth();
const email = ref("");
const password = ref("");
const visible = ref(false);

const login = async () => {
  const response = await useFetch("http://localhost:3000/api/login", {
    method: 'POST',
    body:{
      user:{
      email: email.value,
      password: password.value,
      }
    },
    headers: {
      'Content-Type': 'application/json'
    }
  });
  if (response.error.value) {
    console.error('Login failed:', response.error.value);
  } else {
    signIn(response.data);
  }
};
</script>

<template>
  <div class="bg-grey-lighten-3 pt-10 pb-10">
    <p class="text-h5 text-center">管理者ログインページ</p>
    <v-container>
      <div>
        <v-card class="mx-auto pa-12 pb-8" max-width="448" rounded="lg" flat>
          <form @submit.prevent="login">
            <v-text-field
              v-model="email"
              label="Email address"
              prepend-inner-icon="mdi-email-outline"
              outlined
            ></v-text-field>

            <v-text-field
              v-model="password"
              :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
              :type="visible ? 'text' : 'password'"
              label="Password"
              prepend-inner-icon="mdi-lock-outline"
              outlined
              @click:append-inner="visible = !visible"
            ></v-text-field>
            <v-btn class="mb-8" size="large" color="primary" block type="submit">
              LOG IN
            </v-btn>
          </form>
        </v-card>
      </div>
    </v-container>
  </div>
</template>

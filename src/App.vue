<template>
  <v-app>
    <v-container>
      <v-main>
        <LoginForm/>
      </v-main>
    </v-container>
  </v-app>
</template>

<script>

import LoginForm from "@/components/LoginForm";
export default {
  name: 'App',
  components: {
    LoginForm
  }
}
</script>

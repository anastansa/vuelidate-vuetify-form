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


import LoginForm from "@/components/Login";
export default {
  name: 'App',

  components: {
    LoginForm
  },

  data: () => ({}),
}
</script>

<template>
  <v-row justify="center">
    <v-col cols="5">
      <v-form max-width="500">
        <v-text-field
            clearable
            label="Name"
            prepend-icon="mdi-account-outline"
            variant="underlined"
        ></v-text-field>
        <v-text-field
            clearable
            label="Email"
            prepend-icon="mdi-email-outline"
            variant="underlined"
        ></v-text-field>
        <v-text-field
            clearable
            label="Password"
            prepend-icon="mdi-lock-outline"
            variant="underlined"
            class="mb-10"

        ></v-text-field>
        <v-btn
            color="blue"
        >
          Submit
        </v-btn>
      </v-form>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: "LoginForm"
}
</script>

<style scoped>

</style>

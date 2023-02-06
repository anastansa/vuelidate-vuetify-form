<template>
  <v-row justify="center">
    <v-col cols="11" lg="5">
      <v-form max-width="500" class="pa-8 rounded-lg elevation-2">
        <v-text-field
            v-model="state.name"
            clearable
            label="Name"
            prepend-icon="mdi-account-outline"
            variant="underlined"
        ></v-text-field>
        <p
            v-for="error of v$.name.$errors"
            :key="error.$uid"
        >
          <span class="error">{{ error.$message }}</span>
        </p>
        <v-text-field
            v-model="state.email"
            clearable
            label="Email"
            prepend-icon="mdi-email-outline"
            variant="underlined"
        ></v-text-field>
        <p
            v-for="error of v$.email.$errors"
            :key="error.$uid"
        >
          <span class="error">{{ error.$message }}</span>
        </p>
        <v-text-field
            v-model="state.password.password"
            type="password"
            clearable
            label="Password"
            prepend-icon="mdi-lock-outline"
            variant="underlined"
        ></v-text-field>
        <p
            v-for="error of v$.password.password.$errors"
            :key="error.$uid"
        >
          <span class="error">{{ error.$message }}</span>
        </p>
        <v-text-field
            v-model="state.password.confirm"
            type="password"
            clearable
            label="Repeat password"
            prepend-icon="mdi-lock-outline"
            variant="underlined"
        ></v-text-field>
        <p
            v-for="error of v$.password.confirm.$errors"
            :key="error.$uid"
        >
          <span class="error">{{ error.$message }}</span>
        </p>
        <v-btn
            color="blue"
            class="mt-10"
            @click="onSubmit"
        >
          Submit
        </v-btn>
      </v-form>
    </v-col>
  </v-row>
</template>

<script setup>

import { reactive, computed } from 'vue'
import { useVuelidate } from '@vuelidate/core'
import { required, email, sameAs, minLength } from '@vuelidate/validators'

const state = reactive({
  name: '',
  email: '',
  password: {
    password: '',
    confirm: ''
  }
})

const rules = {
  name: { required },
  email: { required, email },
  password: {
    password: { required, minLength: minLength(6), $autoDirty: true },
    confirm: { required, sameAs: sameAs(computed(() => state.password.password)), $autoDirty: true }
  }
}

const v$ = useVuelidate(rules, state)

const onSubmit = () => {
  v$.value.$touch()

  if (!v$.value.$errors.length) {
    // submit form, then:

    state.name = ''
    state.email = ''
    state.password.password = ''
    state.password.confirm = ''
    v$.value.$reset()
  }
}
</script>

<style scoped>

.error {
  color: red;
  font-size: 14px;
}

</style>

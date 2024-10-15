<script setup>
import { requiredValidator, emailValidator } from '@/utils/validators'
import { ref } from 'vue'

const isPasswordVisible = ref(false)
const refVForm = ref()

// Load Variables
const formDataDefault = {
  email: '',
  password: ''
}
const formData = ref({ ...formDataDefault })

const onSubmit = () => {
  // Add your login logic here, e.g., API call
  console.log('Form submitted:', formData.value)
}

const onFormSubmit = () => {
  refVForm.value?.validate().then(({ valid }) => {
    if (valid) onSubmit()
  })
}
</script>

<template>
  <v-form class="mt-5" ref="refVForm" @submit.prevent="onFormSubmit">
    <v-text-field 
      v-model="formData.email" 
      hint="Enter your e-mail to access this website"
      label="Email"  
      prepend-inner-icon="mdi-email-outline"
      :rules="[requiredValidator, emailValidator]"
      class="purple-input"
    ></v-text-field>

    <v-text-field
      v-model="formData.password"  
      prepend-inner-icon="mdi-lock-outline"
      hint="Enter your password to access this website"
      label="Password"
      :type="isPasswordVisible ? 'text' : 'password'"
      :append-inner-icon="isPasswordVisible ? 'mdi-eye' : 'mdi-eye-off'"
      @click:append-inner="isPasswordVisible = !isPasswordVisible"
      :rules="[requiredValidator]"
      class="purple-input"
    ></v-text-field>

    <v-btn
      class="mt-2"
      type="submit"
      block
      color="purple"
      prepend-icon="mdi-login"
    >
      Log In
    </v-btn>
  </v-form>
</template>

<style>
.purple-input .v-input__control {
  border-bottom: 2px solid purple; /* Adjust the thickness as needed */
}

.purple-input .v-input__control:focus {
  border-bottom: 2px solid purple; /* Change color when focused */
}

.purple-input .v-input__control:hover {
  border-bottom: 2px solid purple; /* Change color on hover */
}
</style>

<script setup>
import {
  requiredValidator,
  emailValidator,
  passwordValidator,
  confirmedValidator
} from '@/utils/validators'
import { ref } from 'vue'

const isPasswordVisible = ref(false)
const isPasswordConfirmVisible = ref(false)
const refVForm = ref()  // Make sure to define ref for the form

// Load Variables
const formDataDefault = {
  firstname: '',
  lastname: '',
  email: '',
  password: '',
  password_confirmation: ''
}
const formData = ref({ ...formDataDefault })

const onSubmit = () => {
  // Add your submit logic here, e.g., API call
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
    <v-row>
      <v-col cols="12" md="6">
        <v-text-field 
          v-model="formData.firstname"
          label="Firstname" 
          :rules="[requiredValidator]"
          class="purple-input"
        ></v-text-field>
      </v-col>

      <v-col cols="12" md="6">
        <v-text-field 
          v-model="formData.lastname"
          label="Lastname"
          :rules="[requiredValidator]"
          class="purple-input"
        ></v-text-field>
      </v-col>

      <v-col cols="12">
        <v-text-field 
          v-model="formData.email"
          label="Email" 
          placeholder="@gmail.com"
          prepend-inner-icon="mdi-email-outline"
          :rules="[requiredValidator, emailValidator]"
          class="purple-input"
        ></v-text-field>
      </v-col>

      <v-col cols="12" md="6">
        <v-text-field
          v-model="formData.password"
          prepend-inner-icon="mdi-lock-outline"
          label="Password"
          :type="isPasswordVisible ? 'text' : 'password'"
          :append-inner-icon="isPasswordVisible ? 'mdi-eye' : 'mdi-eye-off'"
          @click:append-inner="isPasswordVisible = !isPasswordVisible"
          :rules="[requiredValidator, passwordValidator]"
          class="purple-input"
        ></v-text-field>
      </v-col>

      <v-col cols="12" md="6">
        <v-text-field
          v-model="formData.password_confirmation"
          label="Confirm Password"
          :type="isPasswordConfirmVisible ? 'text' : 'password'"
          :append-inner-icon="isPasswordConfirmVisible ? 'mdi-eye' : 'mdi-eye-off'"
          @click:append-inner="isPasswordConfirmVisible = !isPasswordConfirmVisible"
          :rules="[requiredValidator, confirmedValidator(formData.password_confirmation, formData.password)]"
          class="purple-input"
        ></v-text-field>
      </v-col>
    </v-row>

    <v-btn 
      class="mt-2" 
      type="submit"
      block 
      color="purple" 
      prepend-icon="mdi-account-plus"
    >
      Sign up
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

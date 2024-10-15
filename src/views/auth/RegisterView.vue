<script setup>
import AppLayout from '@/components/layout/AppLayout.vue'
import RegisterForm from '@/components/auth/RegisterForm.vue'
import { useDisplay } from 'vuetify'

const { mobile } = useDisplay()
</script>

<template>
  <AppLayout>
    <template #content>
      <v-row class="d-flex justify-center align-center" style="min-height: 80vh;">
        <v-col cols="12" md="6" class="mx-auto pt-16">
          <v-card 
            class="mx-auto" 
            elevation="24" 
            style="background-color: #8E24AA; border-radius: 20px;"
          >
            <v-card-title class="text-center">
              <v-img
                class="mx-auto"
                src="/images/book-logo.png"
                :height="mobile ? '200%' : '150'"
              ></v-img>
              <h2 class="font-weight-black">BOOKBYTE</h2>
              <h5>Registration</h5>
            </v-card-title>

            <v-card-text class="bg-surface-light pt-4">
              <RegisterForm></RegisterForm>

              <h5 class="text-center pt-5">
                Already have an account?
                <RouterLink class="text-purple-lighten-1 bold-text" to="/">
                  Log in here
                </RouterLink>
              </h5>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </template>
  </AppLayout>
</template>

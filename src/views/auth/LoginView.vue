<script setup>
import AppLayout from '@/components/layout/AppLayout.vue'
import { useDisplay } from 'vuetify'

const { mobile } = useDisplay()
</script>

<template>
  <AppLayout>
    <template #content>
      <v-row>
        <v-col cols="12" md="6" class="mx-auto pt-16">
          <v-card class="mx-auto" elevation="24">
            <v-card-title class="text-center">
              <v-img
                class="mx-auto"
                src="/images/book-logo.png"
                :height="mobile ? '250%' : '200'"
              ></v-img>
            </v-card-title>

            <v-card-text class="bg-surface-light pt-4">
              <v-form fast-fail @submit.prevent>
                <v-text-field
                  label="Username"
                  variant="outlined"
                ></v-text-field>

                <v-text-field
                  label="Password"
                  type="password"
                  variant="outlined"
                ></v-text-field>

                <v-btn
                  class="mt-2"
                  type="submit"
                  block
                  color="purple"
                  prepend-icon="mdi-login"
                  >Log In</v-btn
                >
              </v-form>

              <v-divider class="my-5"> </v-divider>

              <h5 class="text-center">
                Don't have an account yet?
                <RouterLink class="text-purple-lighten-2" to="/register"
                  >Sign up here</RouterLink
                >
              </h5>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </template>
  </AppLayout>
</template>

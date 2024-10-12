<script setup>
import { ref } from 'vue'

const theme = ref('dark')

// function onClick() {
//   theme.value = theme.value === 'light' ? 'dark' : 'light'
// }
</script>

<template>
  <v-responsive>
    <v-app :theme="theme">
      <v-app-bar class="px-3" color="grey-lighten-1">
        <v-spacer></v-spacer>

        <!-- <v-btn
          :prepend-icon="
            theme === 'light' ? 'mdi-weather-sunny' : 'mdi-weather-night'
          "
          text="Toggle Theme"
          slim
          @click="onClick"
        ></v-btn> -->
      </v-app-bar>

      <v-main>
        <v-container>
          <slot name="content"></slot>
        </v-container>
      </v-main>

      <!-- <v-footer color="black" border app>2024 - BookByte | All Rights Reserved</v-footer> -->
    </v-app>
  </v-responsive>
</template>

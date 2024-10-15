<script setup>
import { ref, onMounted } from 'vue'

// import { ref, onMounted, computed } from 'vue'

const theme = ref('light')

// Check localStorage for the theme on mount
onMounted(() => {
  const savedTheme = localStorage.getItem('theme')
  if (savedTheme) {
    theme.value = savedTheme
  }
})

// Function to toggle theme
function onToggleTheme() {
  theme.value = theme.value === 'light' ? 'dark' : 'light'
  localStorage.setItem('theme', theme.value)
}

// // Computed property for background style
// const backgroundStyle = computed(() => {
//   return theme.value === 'light' 
//     ? {
//         backgroundImage: 'url("/images/ombreee.jpg")',  // Corrected URL
//         backgroundSize: 'cover',
//         backgroundPosition: 'center'
//       }
//     : {
//         backgroundImage: 'url("/images/ombreee.jpg")',   // Corrected URL
//         backgroundSize: 'cover',
//         backgroundPosition: 'center'
//       }
// })
</script>

<template>
  <v-responsive>
    <v-app :theme="theme">
      <v-app-bar
        class="px-3"
        :color="theme === 'light' ? 'purple-lighten-3' : 'purple-lighten-1'"
        border
      >
        <v-spacer></v-spacer>

        <v-btn
          class="me-2"
          :icon="theme === 'light' ? 'mdi-weather-sunny' : 'mdi-weather-night'"
          variant="elevated"
          color="purple"
          slim
          @click="onToggleTheme"
        ></v-btn>
      </v-app-bar>

      <v-main :style="backgroundStyle">
        <slot name="content"></slot>
      </v-main>

      <v-footer
        class="font-weight-bold d-flex justify-center align-center"
        :color="theme === 'light' ? 'purple-lighten-3' : 'purple-lighten-1'"
        border
        app
      >
        <div :class="mobile ? 'w-100 text-center' : ''">
          Copyright © 2024 - BookByte | All Rights Reserved
        </div>
      </v-footer>
    </v-app>
  </v-responsive>
</template>

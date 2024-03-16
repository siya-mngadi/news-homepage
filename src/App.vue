<template>
  <v-app>
    <v-container>
      <AppHeader />
    </v-container>

    <v-container id="home">
      <HomePage />
    </v-container>
  </v-app>
</template>

<script setup lang="ts">
import AppHeader from '@/components/AppHeader.vue'
import HomePage from '@/components/HomePage.vue'
</script>

<style lang="scss" scoped></style>

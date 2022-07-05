<script setup lang="ts">
import Header from './Header.vue'
import Footer from './Footer.vue'
</script>

<template>
  <div class="wrapper">
    <Header />
    <main class="main"><slot /></main>
    <Footer />
  </div>
</template>

<style lang="scss">
.main {
  padding-top: 85px;
}
</style>
<script setup>
import TopBanner from "./components/TopBanner.vue";
import Navbar from "./components/Navbar.vue";

</script>

<template>
  <div class="container">
    <TopBanner />
    <Navbar />
    <router-view />
  </div>

</template>

<style scoped>
.container {
  max-width: 1280px;
  width: 100%;
  margin: 0 auto;
}
</style>

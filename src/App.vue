<script setup>
import TopBanner from "./components/TopBanner.vue";
import Navbar from "./components/Navbar.vue";
import Footer from "./components/Footer.vue";

</script>

<template>
  <div class="container">
    <TopBanner />
    <Navbar />
    <router-view />
    <Footer />
  </div>

</template>

<style scoped>
.container {
  max-width: 1280px;
  width: 100%;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>

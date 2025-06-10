<template>
  <div class="top-banner">
    Your 2025 Annual Forecast Await You – Exclusively on Astopia!
  </div>
</template>


<style scoped>
.top-banner {
  width: 100vw;
  height: 51px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 15px 10px;
  font-family: "Playfair Display", serif;
  font-size: 16px;
  font-weight: 500;
  line-height: 100%;
  letter-spacing: 0%;
  color: #F9FBFC;
  /* background: linear-gradient(135deg, rgba(255, 255, 255, 0.2), rgba(255, 255, 255, 0.4), rgba(255, 255, 255, 0.2)); */

  background: linear-gradient(135deg,
      rgba(255, 255, 255, 0.15) 0%,
      rgba(255, 255, 255, 0.2) 40%,
      rgba(255, 255, 255, 0.1) 100%);

  backdrop-filter: blur(2px);
  -webkit-backdrop-filter: blur(2px);

  margin-bottom: 50px;
}

@media (max-width: 768px) {
  .top-banner {
    width: 100vw;
    max-width: 100%;
    margin-bottom: 20px;
    font-size: 14px;
    padding: 12px 8px;
  }
}
</style>

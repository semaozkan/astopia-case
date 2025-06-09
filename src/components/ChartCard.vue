<template>
    <div class="card-container">
        <div class="card">
            <img :src="image" alt="Houses Chart" />
            <h3 v-html="title"></h3>
            <p>{{ description }}</p>
        </div>
    </div>
</template>

<script setup>
defineProps({
    image: String,
    title: String,
    description: String
});
</script>

<style scoped>
.card-container {
    display: flex;
}

.card {
    background: linear-gradient(180deg, #151B3B 0%, #1E2859 50%, #0F152F 100%);
    border: 0.75px solid #FBE1C4;
    border-radius: 8px;
    padding: 15px 4px;
    width: 320px;
    min-height: 331px;
}

.card img {
    width: 100%;
    height: auto;
    margin-bottom: 18.83px;
    object-fit: contain;
    filter:
        drop-shadow(0px 3.01px 3.01px rgba(0, 0, 0, 0.25)) drop-shadow(0px 3.01px 10px rgba(255, 255, 255, 1));
}

.card h3 {
    color: #fcdba0;
    font-size: 20px;
    font-weight: 600;
    margin-bottom: 9.79px;
}

.card p {
    font-family: "Poppins", sans-serif;
    font-size: 13.56px;
    line-height: 20px;
    padding: 0 12px;
}
</style>
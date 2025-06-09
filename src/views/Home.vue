<script setup>

</script>

<template>
    <div class="home-container">

        <div class="breadcrumb">
            <img src="../../public/home-2.png" alt="">
            <span class="breadcrumb-label"> > Rising Sign</span>
        </div>

        <div class="rising-section-header">
            <h1><span class="highlight">Rising Sign</span> Calculator</h1>
            <p>Ever feel like the first impression you give isn’t the full story?</p>
            <p>Or wonder why you instinctively react a certain way in new situations?</p>
        </div>
    </div>

</template>

<style scoped>
.home-container {
    width: 100%;
    height: 200vh;
}

.breadcrumb {
    display: flex;
    align-items: center;
    gap: 10px;
    margin: 50px 0;
    padding: 0 50px;
}

.breadcrumb-label {
    font-size: 20px;
}

.rising-section-header {
    text-align: center;
    color: #F9FBFC;
    margin-bottom: 50px;
}

.rising-section-header h1 {
    font-family: "Gloock", serif;
    font-size: 36px;
    font-weight: 400;
    line-height: 100%;
    letter-spacing: 4%;
    margin-bottom: 20px;
}

.rising-section-header .highlight {
    color: rgba(252, 218, 162, 1);
    font-weight: 400;
}

.rising-section-header p {
    font-family: "Poppins", sans-serif;
    font-size: 15px;
    line-height: 100%;
    color: #FFFFFF;
    text-align: center;
}
</style>
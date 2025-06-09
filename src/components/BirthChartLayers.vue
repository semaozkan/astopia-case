<script setup>
import ChartCard from "../components/ChartCard.vue";

const cards = [
    {
        image: new URL('../assets/card1.png', import.meta.url).href,
        title: "Houses in Your Birth Chart",
        description:
            "12 sections of the chart representing different areas of life (career, relationships, home, etc.). Planets in a house show where that energy plays out."
    },
    {
        image: new URL('../assets/card2.png', import.meta.url).href,
        title: "Personal Traits",
        description:
            "Learn your lucky color, number, and gemstone to enhance your personal energy."
    },
    {
        image: new URL('../assets/card3.png', import.meta.url).href,
        title: "Aspects in Your Birth Chart",
        description:
            "Angles between planets showing how their energies interact – revealing dynamics and tensions within you and your life."
    }
];
</script>

<template>
    <section class="chart-layers">
        <h2>Explore the<span> Layers of Your Birth Chart</span></h2>
        <p class="intro">
            Your birth chart is more than just your Sun sign. It provides a deeper understanding of your personality,
            potential, and life journey through the positions of planets in the different houses, the angles (aspects)
            between them, and key factors like your lucky number, color, and gemstone.
        </p>
        <p class="sub-intro">
            Your birth chart has layers that connect to your personal traits:
        </p>

        <div class="card-grid">
            <ChartCard v-for="(card, index) in cards" :key="index" :image="card.image" :title="card.title"
                :description="card.description" />
        </div>


    </section>
</template>

<style scoped>
.chart-layers {
    width: 100vw;
    position: relative;
    text-align: center;
    color: white;
    padding-bottom: 16px;
    z-index: 1;
    overflow: hidden;
    margin-bottom: 60px;
}

.chart-layers::before {
    content: "";
    position: absolute;
    inset: 0;
    background: url("../assets/birth_chart.jpg") no-repeat center center;
    background-size: cover;
    opacity: 0.21;
    z-index: -1;
}

.chart-layers h2 {
    font-size: 36px;
    font-weight: 400;
    margin-bottom: 20px;
}

.chart-layers h2 span {
    color: #FCDAA2;
}

.chart-layers .intro {
    font-family: "Poppins", sans-serif;
    max-width: 962px;
    margin: 0 auto;
    font-size: 18px;
    font-weight: 400;
    line-height: 100%;
}

.chart-layers .sub-intro {
    font-family: "Poppins", sans-serif;
    margin-top: 25px;
    font-size: 18px;
    font-weight: 400;
}

.card-grid {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 44px;
    margin-top: 50px;
}
</style>

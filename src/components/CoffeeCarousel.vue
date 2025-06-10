<template>
    <section class="container">
        <div class="header">
            <h2>Yükselen Burcunu <span>Nasıl Hesaplarsın?</span></h2>
            <p class="subtitle">Your ascendant sign influences many aspects of your life:</p>
        </div>

        <div class="carousel-container">
            <button class="scroll-btn left" @click="moveLeft">‹</button>
            <div class="carousel-wrapper" :style="{ width: `${visibleCards * cardWidthWithGap - 50}px` }">

                <div class="carousel" ref="carouselRef" :style="carouselStyle">
                    <div class="coffee-card" v-for="(coffee, index) in coffeeList" :key="index">
                        <img :src="coffee.image" alt="coffee image">
                        <p class="coffee-name">{{ coffee.title }}</p>
                    </div>
                </div>

            </div>
            <button class="scroll-btn right" @click="moveRight">›</button>
        </div>

    </section>
</template>


<script setup>
import { ref, computed, onMounted, onUnmounted, watch } from 'vue'

const totalCards = computed(() => coffeeList.value.length)
const currentIndex = ref(0)
const visibleCards = ref(getVisibleCards())
const cardWidth = ref(getCardWidth())
const gap = 50


const cardWidthWithGap = computed(() => cardWidth.value + gap)

const maxIndex = computed(() =>
    Math.max(0, totalCards.value - visibleCards.value)
)

const moveLeft = () => {
    if (currentIndex.value > 0) {
        currentIndex.value--
    }
}

const moveRight = () => {
    if (currentIndex.value < maxIndex.value) {
        currentIndex.value++
    }
}

const carouselStyle = computed(() => ({
    transform: `translateX(-${currentIndex.value * cardWidthWithGap.value}px)`
}))

function getVisibleCards() {
    const width = window.innerWidth
    if (width < 640) return 1
    if (width < 1024) return 2
    return 3
}

function getCardWidth() {
    const width = window.innerWidth
    if (width < 873) return 220   // mobil
    if (width < 1024) return 272  // tablet
    return 272                    // masaüstü
}

const handleResize = () => {
    visibleCards.value = getVisibleCards()
    cardWidth.value = getCardWidth()

    if (currentIndex.value > totalCards - visibleCards.value) {
        currentIndex.value = Math.max(0, totalCards - visibleCards.value)
    }
}

const coffeeList = ref([])

const fetchCoffees = async () => {
    try {
        const res = await fetch('https://api.sampleapis.com/coffee/hot')
        const data = await res.json()
        coffeeList.value = data
    } catch (error) {
        console.error('Kahve verileri alınamadı:', error)
    }
}

onMounted(() => {
    fetchCoffees()
    window.addEventListener('resize', handleResize)
})

onUnmounted(() => {
    window.removeEventListener('resize', handleResize)
})

watch(coffeeList, () => {
    visibleCards.value = getVisibleCards()
    cardWidth.value = getCardWidth()

    if (currentIndex.value > totalCards.value - visibleCards.value) {
        currentIndex.value = Math.max(0, totalCards.value - visibleCards.value)
    }
})
</script>

<style scoped>
.container {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-bottom: 80px;
}

.header {
    text-align: center;
    color: white;
    margin-bottom: 50px;
}

.header h2 {
    font-size: 36px;
    font-weight: 400;
    margin-bottom: 25px;
}

.header h2 span {
    color: #FCDAA2;
}

.header p {
    font-family: "Poppins", sans-serif;
    font-size: 18px;
    font-weight: 400;
}

.carousel-container {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 16px;
}

.carousel-wrapper {
    display: flex;
    align-items: center;
    gap: 24px;
    overflow: hidden;
    position: relative;
    width: calc(272px * 3 + 50px * 2);
}

.carousel {
    display: flex;
    align-items: center;
    gap: 50px;
    transition: transform 0.5s ease;
}

.carousel::-webkit-scrollbar {
    display: none;
}

.coffee-card {
    font-family: "Poppins", sans-serif;
    width: 272px;
    height: 272px;
    position: relative;
    border-radius: 50%;
    border: 0.75px solid transparent;
    background-image:
        linear-gradient(#151b3b, #1E2859, #0F152F),
        linear-gradient(180deg, #202A69, #604F6F, #A07374);
    background-origin: border-box;
    background-clip: content-box, border-box;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background-color: rgba(255, 255, 255, 0.05);
}

.coffee-card::before {
    content: "";
    position: absolute;
    width: 100%;
    height: 100%;
    border-radius: 50%;
    background: linear-gradient(180deg, #151b3b, #1E2859, #0F152F);
    z-index: 0;
}

.coffee-card img {
    position: absolute;
    width: 100%;
    height: 100%;
    border-radius: 50%;
    object-fit: cover;
    z-index: 0;
    opacity: 0.2;
}

.coffee-name {
    position: relative;
    z-index: 1;
    color: white;
    font-size: 16px;
    text-align: center;
    padding: 10px;
    font-weight: 500;
}

.scroll-btn {
    font-size: 60px;
    color: #ffffff;
    display: flex;
    align-items: center;
    justify-content: center;
    border: none;
    background-color: transparent;
    cursor: pointer;
}

@media (max-width: 873px) {
    .scroll-btn {
        font-size: 40px;
    }

    .coffee-card {
        width: 220px;
        height: 220px;
    }
}
</style>
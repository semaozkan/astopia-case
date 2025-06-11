<template>
    <!-- desktop navbar -->
    <nav class="navbar" v-if="windowWidth > 768">
        <div class="navbar-left">
            <img class="logo" src="../assets/logo.png" alt="logo" />
            <AlignJustify class="menu-icon" @click="isMobileMenuOpen = !isMobileMenuOpen" />
        </div>

        <div v-if="isMobileMenuOpen || windowWidth > 768" class="navbar-center">
            <ul class="navbar-menu">
                <li>Astrological Reading</li>
                <li>Horoscopes</li>
                <li>Articles</li>
                <li>Topics</li>
            </ul>
        </div>

        <div v-if="isMobileMenuOpen || windowWidth > 768" class="navbar-right">
            <button>Sign Up</button>
        </div>
    </nav>

    <!-- mobile navbar -->
    <nav class="nav" v-else>
        <div class="navbar-mobile">
            <img class="logo" src="../assets/logo.png" alt="logo" />
            <AlignJustify class="menu-icon" @click="isMobileMenuOpen = !isMobileMenuOpen" />
        </div>

        <div v-if="isMobileMenuOpen" class="navbar-mobile-menu">
            <ul>
                <li>Astrological Reading</li>
                <li>Horoscopes</li>
                <li>Articles</li>
                <li>Topics</li>
            </ul>
            <button class="sign-up-button">Sign Up</button>

            <X class="menu-close-icon" @click="isMobileMenuOpen = !isMobileMenuOpen" />
        </div>
    </nav>
</template>


<script setup>
import { ref, watch, onMounted, onUnmounted } from 'vue'
import { AlignJustify, X } from 'lucide-vue-next'

const isMobileMenuOpen = ref(false)
const windowWidth = ref(window.innerWidth)

const updateWidth = () => {
    windowWidth.value = window.innerWidth
}

onMounted(() => {
    window.addEventListener('resize', updateWidth)
})

onUnmounted(() => {
    window.removeEventListener('resize', updateWidth)
})

watch(isMobileMenuOpen, (isOpen) => {
    document.body.style.overflow = isOpen ? 'hidden' : 'auto'
    document.documentElement.style.overflow = isOpen ? 'hidden' : 'auto'
})
</script>

<style scoped>
.navbar {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 44.5px;
    height: 43px;
    flex-wrap: wrap;
    max-width: 1280px;
    margin: 0 auto;
}

.navbar-left {
    display: flex;
    align-items: center;
}

.navbar-left .logo {
    display: flex;
    align-items: center;
    max-width: 120px;
}

.menu-icon {
    cursor: pointer;
    width: 28px;
    height: 28px;
    color: white;
}

.menu-close-icon {
    position: absolute;
    top: 36px;
    right: 36px;
    width: 28px;
    height: 28px;
    cursor: pointer;
    color: white;
}

.navbar-menu {
    width: 526px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    list-style: none;
    padding: 0;
    margin: 0;
    font-size: 14px;
    font-weight: 400;
}

.navbar-menu li {
    cursor: pointer;
}

.navbar-right button,
.sign-up-button {
    width: 151px;
    height: 43px;
    padding: 10px 20px;
    border-radius: 12px;

    background: linear-gradient(90deg,
            rgba(101, 113, 188, 1),
            rgba(38, 62, 120, 1));
    border: 1px solid rgba(32, 24, 67, 1);

    color: white;
    font-family: "Playfair Display", serif;
    font-size: 12px;
    font-weight: 700;

    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;

    box-shadow: inset 4px 4px 4px rgba(249, 251, 252, 0.4);
}

.nav {
    width: 100%;
}

.navbar-mobile {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 24px;
}

.navbar-mobile-menu {
    position: fixed;
    top: 0;
    left: 0;
    z-index: 999;
    width: 100%;
    height: 100vh;
    background-color: rgba(21, 27, 59, 1);
    display: flex;
    gap: 20px;
    flex-direction: column;
    padding: 96px 48px 48px 48px;
}

.navbar-mobile-menu ul {
    font-size: 21px;
    font-weight: 400;
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 10px;
    text-transform: uppercase;
}

@media (max-width: 992px) {
    .navbar-menu {
        width: 100%;
        gap: 36px;
    }

    .navbar-right button {
        width: 120px;
    }
}

@media (max-width: 768px) {
    .menu-icon {
        display: block;
    }
}
</style>
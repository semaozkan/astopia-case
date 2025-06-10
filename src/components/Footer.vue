<template>
    <footer class="footer">
        <div class="footer-container">
            <div class="footer-top">
                <div class="logo-container">
                    <img src="../assets/logo.png" alt="Astropia Logo" class="logo" />
                    <h3 class="footer-slogan">Discover Cosmic Wisdom</h3>
                </div>
                <div class="link-container">
                    <a href="https://astopia.com/tr/iletisim">Contact</a>
                    <a href="https://astopia.com/tr/sss">FAQs</a>
                    <a href="https://astopia.com/tr/hakkimizda">About Us</a>
                    <a href="https://astopia.com/tr/blogs">Blogs</a>
                    <a href="https://astopia.com/tr/burclar">Horoscopes</a>
                </div>
            </div>

            <div class="footer-buttom">
                <div class="footer-media">
                    <div class="social-icons">
                        <a href="https://www.facebook.com/astopiapp">
                            <img src="../assets/facebook.png" alt="facebook">
                        </a>

                        <a href="https://www.instagram.com/astopiatr/">
                            <img src="../assets/instagram.png" alt="instagram">
                        </a>

                        <a href="https://x.com/Astopiatr">
                            <img src="../assets/X.png" alt="X">
                        </a>

                        <a href="https://www.linkedin.com/company/astopia/">
                            <img src="../assets/linkedin.png" alt="linkedin">
                        </a>

                    </div>

                    <div class="store-buttons">
                        <button class="button">
                            <div class="img-container">
                                <img src="../assets/app_store.png" alt="app_store">
                            </div>

                            <div class="button-info">
                                <span class="info">Available on the</span>
                                <span class="app">App Store</span>
                            </div>
                        </button>

                        <button class="button">
                            <div class="img-container">
                                <img src="../assets/google_play.png" alt="google_play">
                            </div>

                            <div class="button-info">
                                <span class="info">GET IT ON</span>
                                <span class="app">Google Play</span>
                            </div>
                        </button>


                    </div>
                </div>
                <div class="copyright">Copyright © 2024 FramerBite. <br> All Rights Reserved</div>
            </div>
        </div>
    </footer>
</template>

<style scoped>
.footer {
    width: 100vw;
    padding: 46.58px 132px;
    position: relative;
    z-index: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    background: linear-gradient(180deg, #151A3D 0%, #1E2758 50%, #0F1530 100%);
}

.footer::before {
    content: "";
    position: absolute;
    inset: 0;
    background-image: url('../assets/footer.jpg');
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
    opacity: 0.15;
    z-index: -1;
}

.footer-container {
    width: 1280px;
    display: flex;
    flex-direction: column;
}

.footer-top {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding-bottom: 21px;
    border-bottom: 0.85px solid rgba(158, 163, 191, 0.5);
}

.logo-container {
    display: flex;
    align-items: center;
}

.logo {
    width: 140px;
    padding-right: 26.78px;

}

.footer-slogan {
    display: flex;
    align-items: center;
    padding-left: 26.78px;
    font-size: 24px;
    font-weight: 400;
    line-height: 31.27px;
    height: 20px;
    border-left: 0.85px solid #E6E8EC;
}

.link-container {
    font-family: "Poppins", sans-serif;
    display: flex;
    gap: 14px;
    font-size: 18px;
    font-weight: 400;
    color: #9EA3BF;
}

.footer-buttom {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-top: 20px;
}

.footer-media {
    display: flex;
    flex-direction: column;
    gap: 20px;
}

.social-icons {
    display: flex;
    gap: 21px;
}

.social-icons img {
    width: 20px;
    height: 20px;
}

.store-buttons {
    display: flex;
    gap: 6px;
}

.button {
    display: flex;
    align-items: center;
    gap: 6px;
    padding: 4px 16px;
    color: #ffffff;
    background-color: #000000;
    border: none;
    border-radius: 8px;
}

.img-container {
    width: 16px;
    height: 16px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

.img-container img {
    width: 100%;
}

.button-info {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
}

.info {
    font-size: 8px;
}

.app {
    font-size: 14px;
}

.copyright {
    max-width: 206px;
    font-family: "Poppins", sans-serif;
    font-size: 18px;
    font-weight: 400;
    color: #9EA3BF;
}

@media (max-width: 1400px) {
    .footer-container {
        width: 100%;
    }
}

@media (max-width: 1200px) {
    .footer-container {
        width: 100%;
    }

    .footer-top {
        flex-direction: column;
        /* align-items: flex-start; */
        gap: 16px;
    }

}

@media (max-width: 768px) {
    .footer {
        padding: 32px 24px;

    }

    .footer-container {
        width: 100%;
    }

    .footer-top {
        flex-direction: column;
        /* align-items: flex-start; */
        gap: 16px;
    }

    .logo-container {
        flex-direction: column;
        gap: 12px;
    }

    .logo {
        padding: 0;
    }

    .footer-slogan {
        padding-left: 0;
        border-left: none;
        font-size: 20px;
        height: auto;
        line-height: 1.4;
    }

    .link-container {
        flex-wrap: wrap;
        gap: 12px 16px;
        font-size: 16px;
    }

    .footer-buttom {
        flex-direction: column;
        gap: 24px;
        margin-top: 32px;
    }

    .footer-media {
        width: 100%;
        align-items: center;
        gap: 16px;
    }

    .store-buttons {
        flex-wrap: wrap;
        gap: 12px;
    }

    .copyright {
        font-size: 14px;
        max-width: 100%;
    }
}

@media (max-width: 576px) {

    .footer-slogan {
        font-size: 16px;
    }

    .link-container {
        gap: 10px;
        font-size: 14px;
    }

    .copyright {
        text-align: center;
    }
}
</style>
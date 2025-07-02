<script setup>
import { useI18n } from 'vue-i18n'
import { ref } from 'vue'
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'

const { t, locale } = useI18n()

// URLs para call-to-action (reemplazar con las URLs reales)
const registerUrl = 'https://coffeelab-a5cd7.web.app/login'
const loginUrl = 'https://coffeelab-a5cd7.web.app/login'

// FAQ items con estado reactivo
const faqItems = ref(t('faq.items'))
const openFaq = ref([false, false, false])
const faqList = t('faq.items', { returnObjects: true })

function toggleFaq(index) {
  openFaq.value[index] = !openFaq.value[index]
}

// Formulario de contacto
const contactForm = ref({
  nombre: '',
  apellidos: '',
  email: '',
  mensaje: ''
})

function handlePlanClick(planType) {
  window.open(registerUrl, '_blank')
}

function handleContactSubmit() {
  alert(t('contact.alert'))
  contactForm.value = {
    nombre: '',
    apellidos: '',
    email: '',
    mensaje: ''
  }
}

function switchLanguage() {
  locale.value = locale.value === 'es' ? 'en' : 'es'
  // Actualizar FAQ al cambiar idioma
  faqItems.value = t('faq.items')
}

const baristaFeatures = t('plans.barista.features', { returnObjects: true })
const ownerFeatures = t('plans.owner.features', { returnObjects: true })
const fullFeatures = t('plans.full.features', { returnObjects: true })
</script>

<template>
  <div id="app">
    <!-- Header -->
    <header class="header">
      <div class="container">
        <div class="logo">
          <img src="/logo.png" alt="Café Lab Logo" class="logo-img">
        </div>
        <div class="nav-container">
          <nav class="nav">
            <a href="#beneficios" class="nav-link primary">{{ t('nav.benefits') }}</a>
            <a href="#planes" class="nav-link primary">{{ t('nav.plans') }}</a>
            <a href="#faq-contacto" class="nav-link primary">{{ t('nav.contacts') }}</a>
            <a :href="loginUrl" class="nav-link primary login" target="_blank">
              <svg class="login-icon icon-person" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/>
                <circle cx="12" cy="7" r="4"/>
              </svg>
              {{ t('nav.login') }}
            </a>
          </nav>
          <button @click="switchLanguage" class="language-button primary">
            {{ t('language') }}
            <svg class="language-icon" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <polyline points="6 9 12 15 18 9"/>
            </svg>
          </button>
        </div>
      </div>
    </header>

    <main>
      <!-- Sección Hero -->
      <section class="hero">
        <div class="container">
          <div class="hero-content">
            <h1 class="hero-title" v-html="t('hero.title')"></h1>
            <div class="hero-right">
              <p class="hero-subtitle">{{ t('hero.subtitle') }}</p>
              <a :href="registerUrl" class="hero-button primary" target="_blank">{{ t('hero.register') }}</a>
            </div>
          </div>
        </div>
      </section>

      <!-- Sección Beneficios -->
      <section id="beneficios" class="beneficios">
        <div class="container">
          <h2 class="beneficios__title" v-html="t('benefits.title')"></h2>
          <div class="beneficios__grid">
            <!-- Card Barista -->
            <div class="beneficio-card">
              <h3 class="beneficio-card__heading">{{ t('benefits.baristaTitle') }}</h3>
              <p class="beneficio-card__text">
                {{ t('benefits.baristaText') }}
              </p>
              <p class="beneficio-card__cta">
                <span class="highlight">{{ t('benefits.baristaCta').split(' ')[0] }}</span>
                <span class="cta-rest">{{ t('benefits.baristaCta').split(' ').slice(1).join(' ') }}</span>
              </p>
              <a :href="registerUrl" class="btn-beneficios" target="_blank">
                {{ t('benefits.baristaBtn') }}
              </a>
            </div>
            <!-- Card Cafetería -->
            <div class="beneficio-card">
              <h3 class="beneficio-card__heading">{{ t('benefits.ownerTitle') }}</h3>
              <p class="beneficio-card__text">
                {{ t('benefits.ownerText') }}
              </p>
              <p class="beneficio-card__cta">
                <span class="highlight">{{ t('benefits.ownerCta').split(' ')[0] }}</span>
                <span class="cta-rest">{{ t('benefits.ownerCta').split(' ').slice(1).join(' ') }}</span>
              </p>
              <a :href="registerUrl" class="btn-beneficios" target="_blank">
                {{ t('benefits.ownerBtn') }}
              </a>
            </div>
          </div>
        </div>
      </section>

      <!-- Sección Datos que respaldan tus decisiones -->
      <section class="data-section">
        <div class="container">
          <h2 class="data-title">{{ t('data.title') }}</h2>
          <p class="data-subtitle">{{ t('data.subtitle') }}</p>

          <div class="data-features">
            <!-- Dashboard de inventario -->
            <div class="feature-row">
              <div class="feature-image">
                <div class="device-mockup">
                  <img src="/dashboard_inventario.png" alt="Dashboard de inventario">
                </div>
              </div>
              <div class="feature-content">
                <h3 class="feature-title">{{ t('data.dashboardTitle') }}</h3>
                <p class="feature-description">
                  {{ t('data.dashboardDesc') }}
                </p>
              </div>
            </div>

            <!-- Curvas de tueste -->
            <div class="feature-row reverse">
              <div class="feature-image">
                <div class="device-mockup">
                  <img src="/curva_tueste.png" alt="Curvas de tueste">
                </div>
              </div>
              <div class="feature-content">
                <h3 class="feature-title">{{ t('data.curveTitle') }}</h3>
                <p class="feature-description">
                  {{ t('data.curveDesc') }}
                </p>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Planes y características -->
      <section id="planes" class="planes-cafetal">
        <div class="planes-cafetal__container">
          <h2 class="planes-cafetal__title">{{ t('plans.title') }}</h2>

          <div class="planes-cafetal__grid">

            <!-- Plan Barista -->
            <div class="planes-cafetal__plan">
              <h3 class="planes-cafetal__plan-title">{{ t('plans.barista.title') }}</h3>
              <div class="planes-cafetal__card">
                <div class="planes-cafetal__price">{{ t('plans.barista.price') }}</div>
                <p class="planes-cafetal__features">{{ t('plans.barista.features') }}</p>
                <button class="planes-cafetal__button" @click="handlePlanClick('barista')">{{ t('plans.barista.button') }}</button>
              </div>
            </div>

            <!-- Plan Owner/Admin -->
            <div class="planes-cafetal__plan">
              <h3 class="planes-cafetal__plan-title">{{ t('plans.owner.title') }}</h3>
              <div class="planes-cafetal__card">
                <div class="planes-cafetal__price">{{ t('plans.owner.price') }}</div>
                <p class="planes-cafetal__features">{{ t('plans.owner.features') }}</p>
                <button class="planes-cafetal__button" @click="handlePlanClick('owner')">{{ t('plans.owner.button') }}</button>
              </div>
            </div>

            <!-- Plan Full -->
            <div class="planes-cafetal__plan">
              <h3 class="planes-cafetal__plan-title">{{ t('plans.full.title') }}</h3>
              <div class="planes-cafetal__card">
                <div class="planes-cafetal__price">{{ t('plans.full.price') }}</div>
                <p class="planes-cafetal__features">{{ t('plans.full.features') }}</p>
                <button class="planes-cafetal__button" @click="handlePlanClick('full')">{{ t('plans.full.button') }}</button>
              </div>
            </div>

          </div>

          <div class="planes-cafetal__footer">
            <p>{{ t('plans.footer') }}</p>
          </div>
        </div>
      </section>

      <!-- Sección de Testimonios -->
      <section class="testimonios">
        <h2>{{ t('testimonials.title') }}</h2>

        <div class="testimonios-contenedor">
          <div class="testimonio">
            <img src="/Martin_guiterrez.jpg" alt="Martin Gutierrez" />
            <h3>{{ t('testimonials.martin.name') }}</h3>
            <p>{{ t('testimonials.martin.text') }}</p>
          </div>

          <div class="testimonio">
            <img src="/Ana_Rivera.jpg" alt="Ana Rivera" />
            <h3>{{ t('testimonials.ana.name') }}</h3>
            <p>{{ t('testimonials.ana.text') }}</p>
          </div>
        </div>

        <div class="calificaciones">
          <div class="opinion">
            <img src="/Rosa.jpeg" alt="Rosa Dominguez" />
            <h4>{{ t('testimonials.rosa.name') }}</h4>
            <p>{{ t('testimonials.rosa.stars') }}</p>
            <span>"{{ t('testimonials.rosa.text') }}"</span>
          </div>
          <div class="opinion">
            <img src="/Miguel.jpeg" alt="Miguel Diaz" />
            <h4>{{ t('testimonials.miguel.name') }}</h4>
            <p>{{ t('testimonials.miguel.stars') }}</p>
            <span>"{{ t('testimonials.miguel.text') }}"</span>
          </div>
        </div>
      </section>

      <!-- Sección FAQ y Contacto -->
      <section id="faq-contacto" class="faq-contact-section">
        <div class="faq-contact-wrapper">
          <!-- Sección de Preguntas Frecuentes -->
          <div class="faq">
            <h2 class="faq-title">{{ t('faq.title') }}</h2>
            <ol class="faq-list">
              <li class="faq-item">
                <strong>{{ t('faq.q1') }}</strong>
                <div class="faq-answer">{{ t('faq.a1') }}</div>
              </li>
              <li class="faq-item">
                <strong>{{ t('faq.q2') }}</strong>
                <div class="faq-answer">{{ t('faq.a2') }}</div>
              </li>
              <li class="faq-item">
                <strong>{{ t('faq.q3') }}</strong>
                <div class="faq-answer">{{ t('faq.a3') }}</div>
              </li>
              <li class="faq-item">
                <strong>{{ t('faq.q4') }}</strong>
                <div class="faq-answer">{{ t('faq.a4') }}</div>
              </li>
            </ol>
            <a href="#" class="ver-mas">{{ t('faq.seeMore') }}</a>
          </div>

          <!-- Sección de Formulario de Contacto -->
          <div class="contact">
            <h2 class="contact-title">{{ t('contact.title') }}</h2>
            <form @submit.prevent="handleContactSubmit">
              <label for="nombre">{{ t('contact.name') }}</label>
              <input type="text" id="nombre" v-model="contactForm.nombre" required>
              
              <label for="apellidos">{{ t('contact.lastname') }}</label>
              <input type="text" id="apellidos" v-model="contactForm.apellidos" required>
              
              <label for="email">{{ t('contact.email') }}</label>
              <input type="email" id="email" v-model="contactForm.email" required>
              
              <label for="mensaje">{{ t('contact.message') }}</label>
              <textarea id="mensaje" v-model="contactForm.mensaje" rows="4" required></textarea>
              
              <button type="submit">{{ t('contact.button') }}</button>
            </form>
          </div>
        </div>
      </section>

      <!-- Footer -->
      <footer class="footer">
        <div class="container">
          <div class="footer-content">
            <div class="footer-section">
              <h3>{{ t('footer.quickLinks') }}</h3>
              <ul>
                <li><a href="#">{{ t('footer.home') }}</a></li>
                <li><a href="#beneficios">{{ t('nav.benefits') }}</a></li>
                <li><a href="#planes">{{ t('nav.plans') }}</a></li>
                <li><a href="#faq-contacto">{{ t('nav.contacts') }}</a></li>
              </ul>
            </div>
            <div class="footer-section">
              <h3>{{ t('footer.resources') }}</h3>
              <ul>
                <li><a href="#">{{ t('footer.blog') }}</a></li>
                <li><a href="#faq-contacto">{{ t('footer.faq') }}</a></li>
                <li><a href="#">{{ t('footer.support') }}</a></li>
              </ul>
            </div>
            <div class="footer-section">
              <h3>{{ t('footer.contact') }}</h3>
              <ul>
                <li><a href="mailto:contacto@cafemetrix.com">contacto@cafemetrix.com</a></li>
                <li><a href="#">{{ t('footer.phone') }}</a></li>
              </ul>
            </div>
            <div class="footer-section">
              <h3>{{ t('footer.aboutUs') }}</h3>
              <ul>
                <li>
                  <a href="https://youtu.be/aaMsFIHMJBY" target="_blank" rel="noopener noreferrer">
                    {{ t('footer.aboutTeam') }}
                    <img src="https://img.youtube.com/vi/aaMsFIHMJBY/hqdefault.jpg" alt="About the team video preview" class="video-preview-img">
                  </a>
                </li>
                <li>
                  <a href="https://youtu.be/Op5L0uSXScE" target="_blank" rel="noopener noreferrer">
                    {{ t('footer.aboutProduct') }}
                    <img src="https://img.youtube.com/vi/Op5L0uSXScE/hqdefault.jpg" alt="About the product video preview" class="video-preview-img">
                  </a>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </footer>
    </main>
  </div>
</template>

<style>
/* Importar fuentes de Google */
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700&display=swap');

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Montserrat', sans-serif;
    line-height: 1.6;
    background-color: #F8F7F2;
    color: #414535;
}

.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

/* ======= HEADER ======= */
.header {
    background-color: #618985;
    padding: 15px 0;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    position: fixed;
    width: 100%;
    top: 0;
    z-index: 1000;
}

.logo {
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #414535;
    border-radius: 50px;
    width: 200px;
    height: 60px;
    overflow: hidden;
}

.logo-img {
    width: 80%;
    height: 80%;
    object-fit: contain;
}

.nav-container {
    display: flex;
    align-items: center;
    gap: 20px;
}

.nav {
    display: flex;
    gap: 20px;
}

.nav-link {
    text-decoration: none;
    font-family: 'Montserrat', sans-serif;
    font-weight: 500;
    font-size: 16px;
    line-height: 22px;
    padding: 10px 15px;
    display: flex;
    align-items: center;
}

/* Botones - Estados según diseño */
.nav-link.primary,
.language-button,
.hero-button.primary {
    background-color: #414535;
    color: #F8F8F8;
    border: 2px solid transparent;
    border-radius: 50px;
    transition: background-color 0.3s, color 0.3s, border 0.3s, box-shadow 0.3s;
    padding: 12px 30px;
}

.language-button {
    text-decoration: none; 
    padding: 12px 20px;     
    border-radius: 30px;    
}

.nav-link.primary:hover,
.language-button:hover,
.hero-button.primary:hover {
    background-color: #F8F8F8;
    color: #414535;
    border: 2px solid transparent;
}

.nav-link.primary:active,
.language-button:active,
.hero-button.primary:active {
    background-color: #F8F8F8;
    color: #414535;
    border: 2px solid #414535;
    box-shadow: none;
}

.nav-link.primary:disabled,
.language-button:disabled,
.hero-button.primary:disabled {
    opacity: 0.5;
    cursor: not-allowed;
}

.login-icon {
    margin-right: 8px;
}

.language-icon {
    margin-left: 8px;
}

/* ======= HERO ======= */
.hero {
    position: relative;
    background-image: url('/hero-background.jpg');
    background-size: cover;
    background-position: center;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding-top: 70px;
    overflow: hidden;
}

.hero::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.6);
    z-index: 1;
}

.hero-content {
    position: relative;
    z-index: 2;
    display: flex;
    justify-content: space-between;
    width: 100%;
    max-width: 1200px;
    padding: 0 20px;
    color: white;
}

.hero-title {
    font-family: 'Montserrat', sans-serif;
    font-weight: 700;
    font-size: 80px;
    line-height: 90px;
    color: #C19875;
    text-transform: uppercase;
    max-width: 50%;
}

.hero-right {
    display: flex;
    flex-direction: column;
    align-items: center;
    max-width: 40%;
}

.hero-subtitle {
    font-family: 'Montserrat', sans-serif;
    font-size: 36px;
    line-height: 44px;
    color: #FFFFFF;
    margin-bottom: 30px;
    text-align: center;
}

.hero-button {
    display: inline-block;
    font-family: 'Montserrat', sans-serif;
    font-weight: 500;
    font-size: 18px;
    line-height: 30px;
    padding: 15px 30px;
    text-decoration: none;
    border-radius: 25px;
}

/* ======= SECCIÓN BENEFICIOS ======= */
.beneficios {
    padding: 80px 0;
    background-color: #F8F7F2;
    padding-bottom: 100px;
}

.beneficios .container {
    flex-direction: column;
}

.beneficios__title {
    font-size: 48px;
    font-weight: 700;
    text-align: center;
    margin-bottom: 60px;
}

.underline {
    text-decoration: underline;
    text-decoration-color: #C19875;
    text-decoration-thickness: 3px;
}

.beneficios__grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 40px;
    max-width: 1000px;
    margin: 0 auto;
}

.beneficio-card {
    background: white;
    padding: 40px;
    border-radius: 20px;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
}

.beneficio-card__heading {
    font-size: 32px;
    font-weight: 600;
    margin-bottom: 20px;
    color: #414535;
}

.beneficio-card__text {
    font-size: 18px;
    line-height: 1.6;
    margin-bottom: 30px;
    color: #666;
}

.beneficio-card__cta {
    font-size: 24px;
    font-weight: 600;
    margin-bottom: 30px;
}

.beneficio-card__cta .highlight {
    color: #C19875;
    font-weight: 700;
}

.cta-rest {
    color: #414535;
}

.btn-beneficios {
    display: inline-block;
    background-color: #414535;
    color: white;
    padding: 15px 30px;
    text-decoration: none;
    border-radius: 25px;
    font-weight: 500;
    transition: background-color 0.3s;
}

.btn-beneficios:hover {
    background-color: #C19875;
}

/* ======= SECCIÓN DATOS ======= */
.data-section {
    padding: 80px 0;
    background-color: white;
}

.data-section .container {
    flex-direction: column;
    align-items: center;
}

.data-title {
    font-size: 48px;
    font-weight: 700;
    text-align: center;
    margin-bottom: 20px;
    color: #414535;
}

.data-subtitle {
    font-size: 24px;
    text-align: center;
    margin-bottom: 60px;
    color: #666;
}

.data-features {
    width: 100%;
}

.feature-row {
    display: flex;
    align-items: center;
    margin-bottom: 80px;
    gap: 60px;
}

.feature-row.reverse {
    flex-direction: row-reverse;
}

.feature-content {
    flex: 1;
}

.feature-title {
    font-size: 36px;
    font-weight: 600;
    margin-bottom: 20px;
    color: #414535;
}

.feature-description {
    font-size: 18px;
    line-height: 1.6;
    color: #666;
}

.feature-image {
    flex: 1;
    display: flex;
    justify-content: center;
}

.device-mockup {
    background: #f5f5f5;
    border-radius: 20px;
    padding: 20px;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
}

.device-mockup img {
    max-width: 100%;
    height: auto;
    border-radius: 10px;
}

/* ======= SECCIÓN PLANES ======= */
#planes {
    padding: 80px 0;
    background-color: #F8F7F2;
}

.planes-cafetal__container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 20px;
}

.planes-cafetal__title {
    font-size: 48px;
    font-weight: 700;
    text-align: center;
    margin-bottom: 60px;
    color: #414535;
}

.planes-cafetal__grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 30px;
    margin-bottom: 40px;
}

.planes-cafetal__plan {
    background: white;
    border-radius: 20px;
    padding: 30px;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease;
}

.planes-cafetal__plan:hover {
    transform: translateY(-10px);
}

.planes-cafetal__plan-title {
    font-size: 24px;
    font-weight: 600;
    margin-bottom: 20px;
    color: #414535;
    text-align: center;
}

.planes-cafetal__card {
    text-align: center;
}

.planes-cafetal__price {
    font-size: 36px;
    font-weight: 700;
    color: #C19875;
    margin-bottom: 20px;
}

.planes-cafetal__features {
    list-style: none;
    margin-bottom: 30px;
}

.planes-cafetal__features li {
    padding: 8px 0;
    font-size: 16px;
    color: #666;
}

.planes-cafetal__button {
    background-color: #414535;
    color: white;
    border: none;
    padding: 15px 30px;
    border-radius: 25px;
    font-weight: 500;
    cursor: pointer;
    transition: background-color 0.3s;
    width: 100%;
}

.planes-cafetal__button:hover {
    background-color: #C19875;
}

.planes-cafetal__footer {
    text-align: center;
    font-size: 18px;
    color: #666;
    max-width: 800px;
    margin: 0 auto;
}

/* ======= SECCIÓN TESTIMONIOS ======= */
.testimonios {
    padding: 80px 20px;
    background-color: white;
    text-align: center;
}

.testimonios h2 {
    font-size: 48px;
    font-weight: 700;
    margin-bottom: 60px;
    color: #414535;
}

.testimonios-contenedor {
    display: flex;
    justify-content: center;
    gap: 40px;
    margin-bottom: 60px;
    flex-wrap: wrap;
}

.testimonio {
    background: #F8F7F2;
    padding: 30px;
    border-radius: 20px;
    max-width: 400px;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
}

.testimonio img {
    width: 80px;
    height: 80px;
    border-radius: 50%;
    margin-bottom: 20px;
    object-fit: cover;
}

.testimonio h3 {
    font-size: 20px;
    font-weight: 600;
    margin-bottom: 15px;
    color: #414535;
}

.testimonio p {
    font-size: 16px;
    line-height: 1.6;
    color: #666;
}

.calificaciones {
    display: flex;
    justify-content: center;
    gap: 40px;
    flex-wrap: wrap;
}

.opinion {
    text-align: center;
    max-width: 200px;
}

.opinion img {
    width: 60px;
    height: 60px;
    border-radius: 50%;
    margin-bottom: 15px;
    object-fit: cover;
}

.opinion h4 {
    font-size: 18px;
    font-weight: 600;
    margin-bottom: 10px;
    color: #414535;
}

.opinion p {
    font-size: 20px;
    margin-bottom: 10px;
}

.opinion span {
    font-size: 14px;
    color: #666;
    font-style: italic;
}

/* ======= SECCIÓN FAQ Y CONTACTO ======= */
.faq-contact-section {
    padding: 80px 20px;
    background-color: #F8F7F2;
}

.faq-contact-wrapper {
    max-width: 1200px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 60px;
}

.faq {
    background: white;
    padding: 40px;
    border-radius: 20px;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
}

.faq-title, .contact-title {
    font-size: 32px;
    font-weight: 600;
    margin-bottom: 30px;
    color: #414535;
}

.faq-item {
    margin-bottom: 20px;
}

.question {
    font-size: 18px;
    font-weight: 500;
    color: #414535;
    cursor: pointer;
    padding: 15px 0;
    border-bottom: 1px solid #eee;
    transition: color 0.3s;
}

.question:hover {
    color: #C19875;
}

.answer {
    font-size: 16px;
    color: #666;
    padding: 15px 0;
    line-height: 1.6;
}

.ver-mas {
    color: #C19875;
    text-decoration: none;
    font-weight: 500;
    display: inline-block;
    margin-top: 20px;
}

.contact {
    background: white;
    padding: 40px;
    border-radius: 20px;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
}

.contact form {
    display: flex;
    flex-direction: column;
    gap: 20px;
}

.contact input, .contact textarea {
    padding: 15px;
    border: 2px solid #eee;
    border-radius: 10px;
    font-size: 16px;
    transition: border-color 0.3s;
}

.contact input:focus, .contact textarea:focus {
    outline: none;
    border-color: #C19875;
}

.contact button {
    background-color: #414535;
    color: white;
    border: none;
    padding: 15px 30px;
    border-radius: 25px;
    font-weight: 500;
    cursor: pointer;
    transition: background-color 0.3s;
}

.contact button:hover {
    background-color: #C19875;
}

/* ======= FOOTER ======= */
.footer {
    background-color: #414535;
    color: white;
    padding: 40px 0;
}

.footer .container {
    flex-direction: column;
    align-items: flex-start;
}

.footer-content {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 40px;
    width: 100%;
}

.footer-section h3 {
    font-size: 20px;
    font-weight: 600;
    margin-bottom: 20px;
}

.footer-section ul {
    list-style: none;
}

.footer-section ul li a {
    color: #ccc;
    text-decoration: none;
    line-height: 2;
    transition: color 0.3s;
}

.footer-section ul li a:hover {
    color: #C19875;
}

.video-preview-img {
  width: 100%;
  max-width: 200px;
  border-radius: 8px;
  margin-top: 8px;
  border: 1px solid #555;
  transition: transform 0.3s;
}

.video-preview-img:hover {
  transform: scale(1.05);
}

/* ======= RESPONSIVE ======= */
@media (max-width: 1200px) {
    .faq-contact-wrapper {
        grid-template-columns: 1fr;
        gap: 40px;
    }
    
    .faq, .contact {
        max-width: 600px;
        margin: 0 auto;
    }
}

@media (max-width: 768px) {
    .header .container {
        flex-direction: column;
        gap: 20px;
    }
    
    .hero-content {
        flex-direction: column;
        text-align: center;
        align-items: center;
    }
    
    .hero-title {
        font-size: 48px;
        line-height: 56px;
        margin-bottom: 30px;
    }
    
    .hero-right {
        max-width: 100%;
    }
    
    .hero-subtitle {
        font-size: 24px;
    }

    .beneficios__grid {
      grid-template-columns: 1fr;
    }
    
    .feature-row,
    .feature-row.reverse {
        flex-direction: column;
        text-align: center;
    }
    
    .data-title {
        font-size: 36px;
    }
    
    .data-subtitle {
        font-size: 20px;
    }
    
    .feature-title {
        font-size: 28px;
    }
    
    .feature-description {
        font-size: 16px;
    }
    
    .faq-contact-wrapper {
        grid-template-columns: 1fr;
    }
    
    .faq {
        padding: 30px;
    }
    
    .contact form {
        gap: 15px;
    }
    
    .contact input, .contact textarea {
        padding: 12px;
    }
    
    .testimonios-contenedor, .calificaciones {
        flex-direction: column;
        align-items: center;
    }
    
    .testimonio, .opinion {
        max-width: 100%;
    }
    
    .testimonios h2 {
        font-size: 36px;
    }
    
    .testimonio h3 {
        font-size: 18px;
    }
    
    .testimonio p {
        font-size: 14px;
    }
}

@media (max-width: 600px) {
    .faq-contact-section {
        padding: 40px 20px;
    }
    
    .faq-contact-wrapper {
        gap: 30px;
    }
    
    .faq-title, .contact-title {
        font-size: 28px;
    }
    
    .question {
        font-size: 16px;
    }
    
    .answer {
        font-size: 14px;
    }
}
</style>

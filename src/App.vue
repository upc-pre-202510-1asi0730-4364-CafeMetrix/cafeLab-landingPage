<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
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
            <a href="#beneficios" class="nav-link primary">Beneficios</a>
            <a href="#planes" class="nav-link primary">Planes</a>
            <a href="#faq-contacto" class="nav-link primary">Contactos</a>
            <a :href="loginUrl" class="nav-link primary login" target="_blank">
              <svg class="login-icon icon-person" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/>
                <circle cx="12" cy="7" r="4"/>
              </svg>
              Iniciar sesión
            </a>
          </nav>
          <a href="#language" class="language-button primary">
            ES
            <svg class="language-icon" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <polyline points="6 9 12 15 18 9"/>
            </svg>
          </a>
        </div>
      </div>
    </header>

    <main>
      <!-- Sección Hero -->
      <section class="hero">
        <div class="container">
          <div class="hero-content">
            <h1 class="hero-title">DOMINIO TOTAL SOBRE TU CAFÉ.</h1>
            <div class="hero-right">
              <p class="hero-subtitle">Descubre lo que Café Lab tiene para ofrecerte</p>
              <a :href="registerUrl" class="hero-button primary" target="_blank">Quiero registrarme</a>
            </div>
          </div>
        </div>
      </section>

      <!-- Sección Beneficios -->
      <section id="beneficios" class="beneficios">
        <div class="container">
          <h2 class="beneficios__title">
            Enfoque en <span class="underline">beneficios claros</span>.
          </h2>
          <div class="beneficios__grid">
            <!-- Card Barista -->
            <div class="beneficio-card">
              <h3 class="beneficio-card__heading">Soy barista</h3>
              <p class="beneficio-card__text">
                Documenta tus recetas, eleva tu técnica y construye un perfil sensorial único que defina tu estilo como profesional.
              </p>
              <p class="beneficio-card__cta">
                <span class="highlight">Perfecciona</span>
                <span class="cta-rest">tu arte.</span>
              </p>
              <a :href="registerUrl" class="btn-beneficios" target="_blank">
                Ver herramientas para baristas
              </a>
            </div>
            <!-- Card Cafetería -->
            <div class="beneficio-card">
              <h3 class="beneficio-card__heading">Tengo una cafetería</h3>
              <p class="beneficio-card__text">
                Optimiza tu inventario, garantiza la trazabilidad de tus productos y profesionaliza cada aspecto de tu operación cafetera.
              </p>
              <p class="beneficio-card__cta">
                <span class="highlight">Impulsa</span>
                <span class="cta-rest">tu negocio.</span>
              </p>
              <a :href="registerUrl" class="btn-beneficios" target="_blank">
                Ver soluciones para negocios
              </a>
            </div>
          </div>
        </div>
      </section>

      <!-- Sección Datos que respaldan tus decisiones -->
      <section class="data-section">
        <div class="container">
          <h2 class="data-title">Datos que respaldan tus decisiones.</h2>
          <p class="data-subtitle">Desde la curva hasta el inventario, Café Lab documenta cada paso.</p>

          <div class="data-features">
            <!-- Dashboard de inventario -->
            <div class="feature-row">
              <div class="feature-image">
                <div class="device-mockup">
                  <img src="/dashboard_inventario.png" alt="Dashboard de inventario">
                </div>
              </div>
              <div class="feature-content">
                <h3 class="feature-title">Dashboard de inventario</h3>
                <p class="feature-description">
                  Seguimiento de lotes en tiempo real, stock de granos, y control de movimientos.
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
                <h3 class="feature-title">Curvas de tueste</h3>
                <p class="feature-description">
                  Control preciso del desarrollo del tueste para maximizar las cualidades sensoriales de cada origen.
                </p>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Planes y características -->
      <section id="planes" class="planes-cafetal">
        <div class="planes-cafetal__container">
          <h2 class="planes-cafetal__title">Escala tu café con herramientas a tu medida.</h2>
          
          <div class="planes-cafetal__grid">
            <!-- Plan 1 -->
            <div class="planes-cafetal__plan">
              <h3 class="planes-cafetal__plan-title">Plan Base Cafetal</h3>
              <div class="planes-cafetal__card">
                <div class="planes-cafetal__price">s/.19/mes</div>
                <ul class="planes-cafetal__features">
                  <li>✓ Registro básico de tuestes (manual).</li>
                  <li>✓ Biblioteca de recetas y módulos.</li>
                  <li>✓ Registro de defectos comunes.</li>
                  <li>✓ Guía de almacenamiento y control simple de inventario.</li>
                  <li>✓ Acceso desde móvil.</li>
                </ul>
                <button class="planes-cafetal__button" @click="handlePlanClick('base')">Conocer Plan Base Cafetal</button>
              </div>
            </div>
            
            <!-- Plan 2 -->
            <div class="planes-cafetal__plan">
              <h3 class="planes-cafetal__plan-title">Plan Técnico de Tueste</h3>
              <div class="planes-cafetal__card">
                <div class="planes-cafetal__price">s/.49/mes</div>
                <ul class="planes-cafetal__features">
                  <li>✓ Todo Plan Base Cafetal.</li>
                  <li>✓ Costos automatizados y comparativo por lote.</li>
                  <li>✓ Registro digital de tuestes con curvas personalizadas.</li>
                  <li>✓ Calculadora de pérdida de peso y rendimiento.</li>
                  <li>✓ Biblioteca extendida de perfiles y curvas por origen.</li>
                </ul>
                <button class="planes-cafetal__button" @click="handlePlanClick('tecnico')">Conocer Plan Técnico de Tueste</button>
              </div>
            </div>
            
            <!-- Plan 3 -->
            <div class="planes-cafetal__plan">
              <h3 class="planes-cafetal__plan-title">Plan Artista del Tueste</h3>
              <div class="planes-cafetal__card">
                <div class="planes-cafetal__price">s/.59/mes</div>
                <ul class="planes-cafetal__features">
                  <li>✓ Gestor de recetas personalizadas por método y bebida.</li>
                  <li>✓ Calibrador de molinos y ratio.</li>
                  <li>✓ Portafolio con notas por cliente, origen o evaluación.</li>
                  <li>✓ Registro de extracciones y resultados.</li>
                </ul>
                <button class="planes-cafetal__button" @click="handlePlanClick('artista')">Conocer Plan Artista del Tueste</button>
              </div>
            </div>
            
            <!-- Plan 4 -->
            <div class="planes-cafetal__plan">
              <h3 class="planes-cafetal__plan-title">Plan D' Especialidad</h3>
              <div class="planes-cafetal__card">
                <div class="planes-cafetal__price">s/.81/mes</div>
                <ul class="planes-cafetal__features">
                  <li>✓ Control de inventario (verde y tostado).</li>
                  <li>✓ Conectividad con sensores IoT (tostadoras).</li>
                  <li>✓ Modelado y control sensorial.</li>
                  <li>✓ Módulos de certificaciones y capacitaciones.</li>
                </ul>
                <button class="planes-cafetal__button" @click="handlePlanClick('especialidad')">Conocer Plan D' Especialidad</button>
              </div>
            </div>
          </div>
          
          <div class="planes-cafetal__footer">
            <p>Todos nuestros planes incluyen documentación técnica, soporte personalizado y visualizaciones intuitivas para baristas y cafeterías.</p>
          </div>
        </div>
      </section>

      <!-- Sección de Testimonios -->
      <section class="testimonios">
        <h2>Esto dicen los que ya usan Café Lab.</h2>

        <div class="testimonios-contenedor">
          <div class="testimonio">
            <img src="/Martin_guiterrez.jpg" alt="Martin Gutierrez" />
            <h3>Martin Gutierrez - Dueño de cafetería</h3>
            <p>"Gracias a CafeLab pude optimizar mis procesos mediante documentaciones intuitivas, lo que mejoró mis planificaciones."</p>
          </div>

          <div class="testimonio">
            <img src="/Ana_Rivera.jpg" alt="Ana Rivera" />
            <h3>Ana Rivera - Barista en Lima</h3>
            <p>"CafeLab me ayudó a estandarizar mis tuestes y reducir errores. Ahora todos en la cafetería usan la misma receta."</p>
          </div>
        </div>

        <div class="calificaciones">
          <div class="opinion">
            <img src="/Rosa.jpeg" alt="Rosa Dominguez" />
            <h4>Rosa Dominguez</h4>
            <p>⭐⭐⭐⭐⭐</p>
            <span>"Útil, fácil de usar"</span>
          </div>
          <div class="opinion">
            <img src="/Miguel.jpeg" alt="Miguel Diaz" />
            <h4>Miguel Diaz</h4>
            <p>⭐⭐⭐⭐⭐</p>
            <span>"Rentable"</span>
          </div>
        </div>
      </section>

      <!-- Sección FAQ y Contacto -->
      <section id="faq-contacto" class="faq-contact-section">
        <div class="faq-contact-wrapper">
          <!-- Sección de Preguntas Frecuentes -->
          <div class="faq">
            <h2 class="faq-title">Preguntas Frecuentes (FAQ)</h2>
            <div class="faq-item" v-for="(item, index) in faqItems" :key="index">
              <p class="question" @click="toggleFaq(index)">{{ item.question }}</p>
              <p class="answer" v-show="item.isOpen">{{ item.answer }}</p>
            </div>
            <a href="#" class="ver-mas">Ver más...</a>
          </div>

          <!-- Sección de Formulario de Contacto -->
          <div class="contact">
            <h2 class="contact-title">Contáctanos</h2>
            <form @submit.prevent="handleContactSubmit">
              <label for="nombre">Nombre</label>
              <input type="text" id="nombre" v-model="contactForm.nombre" required>
              
              <label for="apellidos">Apellidos</label>
              <input type="text" id="apellidos" v-model="contactForm.apellidos" required>
              
              <label for="email">Correo electrónico</label>
              <input type="email" id="email" v-model="contactForm.email" required>
              
              <label for="mensaje">Mensaje</label>
              <textarea id="mensaje" v-model="contactForm.mensaje" rows="4" required></textarea>
              
              <button type="submit">Enviar</button>
            </form>
          </div>
        </div>
      </section>

      <!-- Footer -->
      <footer class="footer">
        <div class="container">
          <div class="footer-content">
            <div class="footer-section">
              <h3>Enlaces rápidos</h3>
              <ul>
                <li><a href="#">Inicio</a></li>
                <li><a href="#beneficios">Beneficios</a></li>
                <li><a href="#planes">Planes</a></li>
                <li><a href="#faq-contacto">Contactos</a></li>
              </ul>
            </div>
            <div class="footer-section">
              <h3>Recursos</h3>
              <ul>
                <li><a href="#">Blog</a></li>
                <li><a href="#faq-contacto">FAQ</a></li>
                <li><a href="#">Soporte</a></li>
              </ul>
            </div>
            <div class="footer-section">
              <h3>Contacto</h3>
              <ul>
                <li><a href="mailto:contacto@cafemetrix.com">contacto@cafemetrix.com</a></li>
                <li><a href="#">Teléfono: 123-456-789</a></li>
              </ul>
            </div>
            <div class="footer-section">
              <h3>Sobre Nosotros</h3>
              <ul>
                <li>
                  <a href="https://youtu.be/aaMsFIHMJBY" target="_blank" rel="noopener noreferrer">
                    About the Team
                    <img src="https://img.youtube.com/vi/aaMsFIHMJBY/hqdefault.jpg" alt="About the team video preview" class="video-preview-img">
                  </a>
                </li>
                <li>
                  <a href="https://youtu.be/Op5L0uSXScE" target="_blank" rel="noopener noreferrer">
                    About the Product
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

<script>
export default {
  name: 'App',
  data() {
    return {
      // URLs para call-to-action (reemplazar con las URLs reales)
      registerUrl: 'https://coffeelab-a5cd7.web.app/login', // Reemplazado
      loginUrl: 'https://coffeelab-a5cd7.web.app/login', // Reemplazado
      
      // FAQ items con estado reactivo
      faqItems: [
        {
          question: '¿Puedo usar Cafelab si solo soy barista y no tengo cafetería?',
          answer: '¡Claro! Cafelab se adapta tanto a baristas individuales como a cafeterías completas.',
          isOpen: false
        },
        {
          question: '¿Qué diferencia hay entre los planes?',
          answer: 'Los planes difieren en cantidad de usuarios, acceso a funciones avanzadas y módulos de análisis.',
          isOpen: false
        },
        {
          question: '¿La app está disponible para móvil?',
          answer: 'Sí, Cafelab funciona perfectamente desde navegador móvil. La app nativa está en desarrollo.',
          isOpen: false
        }
      ],
      
      // Formulario de contacto
      contactForm: {
        nombre: '',
        apellidos: '',
        email: '',
        mensaje: ''
      }
    }
  },
  methods: {
    // Manejar clic en planes
    handlePlanClick(planType) {
      console.log(`Plan seleccionado: ${planType}`);
      // Aquí puedes agregar lógica para redirigir al registro con el plan específico
      window.open(this.registerUrl, '_blank');
    },
    
    // Toggle FAQ items
    toggleFaq(index) {
      this.faqItems[index].isOpen = !this.faqItems[index].isOpen;
    },
    
    // Manejar envío del formulario de contacto
    handleContactSubmit() {
      console.log('Formulario enviado:', this.contactForm);
      // Aquí puedes agregar lógica para enviar el formulario
      alert('¡Gracias por tu mensaje! Te contactaremos pronto.');
      
      // Limpiar formulario
      this.contactForm = {
        nombre: '',
        apellidos: '',
        email: '',
        mensaje: ''
      };
    }
  }
}
</script>

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

# CaféLab Landing Page

Landing page moderna para CaféLab construida con Vue 3 + Vite.

## Características

- 🎨 Diseño moderno y responsive
- ☕ Landing page completa para plataforma de café de especialidad
- 📱 Optimizada para móviles
- ⚡ Construida con Vue 3 y Vite para máximo rendimiento
- 🎯 Call-to-action para registro e inicio de sesión
- 📋 Formulario de contacto funcional
- ❓ Sección FAQ interactiva
- 💳 Sección de planes con precios

## Personalización de URLs

Para personalizar las URLs de call-to-action, edita el archivo `src/App.vue` y modifica estas variables en la sección `data()`:

```javascript
data() {
  return {
    // URLs para call-to-action (reemplazar con las URLs reales)
    registerUrl: '#', // Reemplazar con URL de registro
    loginUrl: '#', // Reemplazar con URL de login
    // ... resto del código
  }
}
```

### Ejemplo de configuración:

```javascript
registerUrl: 'https://app.cafelab.com/register',
loginUrl: 'https://app.cafelab.com/login',
```

## Instalación y desarrollo

```bash
# Instalar dependencias
npm install

# Ejecutar en modo desarrollo
npm run dev

# Construir para producción
npm run build

# Previsualizar build de producción
npm run preview
```

## Estructura del proyecto

```
src/
├── App.vue          # Componente principal de la landing page
├── main.js          # Punto de entrada de la aplicación
└── basic/           # Archivos originales HTML/CSS/JS
    ├── index.html
    ├── assets/
    │   ├── css/
    │   ├── js/
    │   └── img/
    └── README.md

public/              # Archivos estáticos (imágenes)
├── logo.png
├── hero-background.jpg
├── dashboard_inventario.png
├── curva_tueste.png
└── ... (otras imágenes)
```

## Tecnologías utilizadas

- **Vue 3** - Framework de JavaScript progresivo
- **Vite** - Herramienta de construcción rápida
- **CSS3** - Estilos modernos con Flexbox y Grid
- **Google Fonts** - Fuente Montserrat

## Funcionalidades implementadas

- ✅ Navegación suave entre secciones
- ✅ FAQ interactivo con toggle
- ✅ Formulario de contacto con validación
- ✅ Botones de call-to-action configurables
- ✅ Diseño responsive completo
- ✅ Efectos hover y transiciones
- ✅ Optimización de imágenes

## Personalización adicional

### Colores principales
- Verde principal: `#414535`
- Verde header: `#618985`
- Marrón acento: `#C19875`
- Fondo: `#F8F7F2`

### Fuentes
- Familia: Montserrat
- Pesos: 400, 500, 600, 700

## Soporte

Para soporte técnico o consultas sobre personalización, contacta al equipo de desarrollo.

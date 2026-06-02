# SPEC.md — Mecánica Oscar: MotoForge

## 1. Concept & Vision

**"MotoForge"** — Un taller de mecánica de motos que fusiona la potencia bruta del two-wheeled engineering con la precisión del futurismo industrial. La web transmite: **fuerza, velocidad, tecnología de punta y confianza profesional**. Visuales oscuros con acentos de fuego y metal fundido. El usuario debe sentir que está entrando al hangar de un ingeniero de carreras, no a un taller cualquiera.

## 2. Design Language

### Aesthetic Direction
**Dark Industrial Futurism** — Inspirado en talleres de MotoGP mezclados con interfaces HUD de ciencia ficción. Metal oscuro, chispas, neón cálido, líneas de ingeniería. Texturas de carbono y acero cepillado.

### Color Palette
- **Background Primary:** `#0a0a0a` (negro profundo)
- **Background Secondary:** `#111111` (gris-carbon)
- **Background Cards:** `#1a1a1a`
- **Accent Primary (Fire Orange):** `#ff6b00`
- **Accent Glow:** `#ff9500` (naranja incandescente)
- **Accent Secondary (Ember):** `#cc4400`
- **Text Primary:** `#ffffff`
- **Text Secondary:** `#888888`
- **Border/Lines:** `#2a2a2a`
- **Glow Effect:** `rgba(255, 107, 0, 0.4)`

### Typography
- **Display / Headings:** `Orbitron` (Google Fonts) — geométrica, futurista, bold
- **Body / Subheadings:** `Rajdhani` (Google Fonts) — técnica, legible, semi-bold
- **Fallback:** `system-ui, sans-serif`

### Spatial System
- Base unit: 8px
- Section padding: 80px–120px vertical
- Card padding: 24px–32px
- Max content width: 1200px
- Grid: 12 columns, 24px gutter

### Motion Philosophy
- **Scroll reveal:** elementos aparecen con fade-up suave (opacity 0→1, translateY 30px→0, 600ms ease-out)
- **Hover glow:** bordes y sombras en naranja con transición de 300ms
- **Parallax sutil:** background con movimiento ligero al scroll
- **Hero typing effect:** texto del headline con efecto typewriter
- **Card lift:** translateY -8px + box-shadow glow al hover

### Visual Assets
- **Icon style:** Line icons con stroke 1.5px, color naranja sobre fondo oscuro
- **Textures:** Subtle carbon fiber pattern en sections alternas
- **Decorative:** Líneas diagonales estilo ingeniería, puntos/gridsHUD

## 3. Layout & Structure

### Page Flow
```
[NAV] — Logo + links, sticky, transparente → sólido al scroll
[HERO] — Full viewport, video/imagen moto en contexto oscuro, headline impactante, CTA
[SERVICIOS] — Grid de 3-4 cards con iconos, descripción de servicios (consultas + cursos)
[CATÁLOGO CURSOS] — Showcase de productos/cursos con precios y CTA
[SOBRE NOSOTROS] — Breve sección con estadísticas del taller (años, clientes, modelos)
[CTA FINAL] — Llamada a consulta/contacto con formulario o WhatsApp
[FOOTER] — Info de contacto, redes, horarios
```

### Responsive Strategy
- Desktop-first con breakpoints en 1024px, 768px, 480px
- Nav → hamburger menu en mobile
- Grid cards: 3 cols → 2 cols → 1 col

## 4. Features & Interactions

### Navigation
- Logo izquierda, links centro/derecha
- Scroll behavior: transparente → `background: #0a0a0a` con blur
- Links: hover underline animado naranja
- CTA button "Contactar" destacado

### Hero Section
- Background: imagen de alta calidad de moto en taller oscuro (generada)
- Overlay gradient negro
- Headline: "POTENCIA. PRECISIÓN. PASIÓN." con efecto glow
- Subheadline: descripción corta del taller
- CTA: "Explorar Servicios" + "Ver Cursos"
- Flecha animada hacia abajo

### Servicios Section
- Título: "NUESTROS SERVICIOS" con línea decorativa naranja
- Cards: Diagnóstico, Mantenimiento, Reparación, Consultas Técnicas
- Cada card: icono, título, descripción, precio referencial
- Hover: borde naranja + lift effect

### Catálogo / Cursos
- Cards de cursos/productos con:
  - Imagen del producto
  - Título del curso
  - Descripción corta
  - Precio
  - Botón "Solicitar Info"
- Diseño tipo "tarjeta de producto premium"

### Stats Section
- Fondo con textura carbon fiber
- Números grandes animados (count-up):
  - "+15 Años de experiencia"
  - "+2,000 Motos atendidas"
  - "+50 Modelos dominados"
  - "24/7 Soporte técnico"

### Contact CTA
- Formulario simple: nombre, email, mensaje
- O alternativa: botón WhatsApp grande
- Diseño tipo HUD futurista

### Footer
- Logo
- Links rápidos
- Datos de contacto
- Redes sociales (Instagram, TikTok, YouTube)
- Horario de atención

## 5. Component Inventory

### Navbar
- Default: transparente, texto blanco, logo
- Scrolled: fondo sólido #0a0a0a, sombra sutil
- Mobile: hamburger → overlay menu

### Button Primary
- Background: `#ff6b00`
- Text: blanco, bold, uppercase, tracking wide
- Hover: brightness 1.2, box-shadow glow naranja
- Active: scale 0.98

### Button Secondary (Ghost)
- Border: 1px solid `#ff6b00`
- Text: `#ff6b00`
- Hover: background `#ff6b00`, text blanco

### Service Card
- Background: `#1a1a1a`
- Border: 1px solid `#2a2a2a`
- Hover: border `#ff6b00`, transform translateY(-8px), shadow glow
- Icon: 48px, stroke naranja

### Product Card
- Imagen 16:9 con overlay gradient
- Badge de categoría (ej: "POPULAR", "NUEVO")
- Título bold, descripción, precio grande en naranja
- CTA button completo

### Form Input
- Background: `#1a1a1a`
- Border: 1px solid `#2a2a2a`
- Focus: border `#ff6b00`, glow sutil
- Placeholder: `#555`

### Section Title
- Font: Orbitron, uppercase, bold
- Decoración: línea horizontal naranja a la izquierda
- Subtítulo en gris debajo

## 6. Technical Approach

### Stack
- **HTML5** semántico
- **CSS3** (custom properties, grid, flexbox, animations)
- **Vanilla JS** (smooth scroll, intersection observer para animaciones, mobile menu)
- **No frameworks** — código limpio y portable

### Performance
- Critical CSS inline
- Google Fonts con `display=swap`
- Imágenes optimizadas (WebP donde posible)
- Lazy loading en imágenes below the fold

### File Structure
```
moto-forge/
├── index.html
├── spec.md
├── assets/
│   └── (imágenes generadas)
└── README.md (opcional)
```

### Accessibility
- Contrast ratios WCAG AA
- Focus states visibles
- Semantic HTML (nav, main, section, article, footer)
- Alt text en todas las imágenes
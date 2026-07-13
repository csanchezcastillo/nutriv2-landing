# Estructura de la Landing Page - nutrif/index.html

> Documento generado el 13 jul 2026. Total: **1538 líneas**.

---

## 📐 Estructura General

```
nutrifit/index.html (1538 líneas)
├── HEAD (líneas 1-1242)
│   ├── Meta tags
│   ├── CSS reset y base
│   ├── Componentes CSS (hero, products, testimonials, etc.)
│   └── JavaScript (reveal + tracking)
└── BODY (líneas 1244-1521)
    ├── Hero
    ├── El Combo Completo Incluye
    ├── Bonuses (con cinta amarilla)
    ├── Pricing Box
    ├── FAQ
    ├── Testimonios
    ├── Garantía
    ├── Footer
    └── Scripts
```

---

## 🎯 Secciones en Orden

### 1. Hero Section (líneas 1226-1250)

- **H1:** "Transforma tu alimentación y alcanza tu peso ideal con el Combo más completo"
- **Micro-copy** (italic, gris): "Tu cuerpo cambia cuando cambias el método"
- **Imagen** del combo (PNG de CloudFront)
- **CTA principal:** "¡SÍ, QUIERO EL COMBO AHORA!" (verde con pulseGlow)

### 2. El Combo Completo Incluye (líneas 1252-1305)

- **H3:** "EL COMBO COMPLETO INCLUYE:"
- **3 product cards:**
  - Reto Keto 21 días
  - 30 Batidos para Quemar Grasa
  - Menús Saludables 7 Días
- **CTA:** "¡SÍ, QUIERO EL COMBO AHORA!"

### 3. Bonuses Section (líneas 1306-1322)

- **H2:** "CON EL COMBO" / "LLEVA GRATIS" (gradient naranja) / "2 BONOS DE REGALO"
- **Background:** gradient blanco-amarillo-blanco con fade
- **2 bonus cards** con cinta amarilla "🎁 BONO #1" / "🎁 BONO #2":
  - 🎁 Guía de Ayuno Intermitente
  - 🎁 Audiolibro "Ayuno Intermitente"
- **Imagen** del combo

### 4. Pricing Box (líneas 1334-1373)

- Card premium con gradient verde oscuro
- Decoraciones radiales (glows)
- Badge "⚡ OFERTA ESPECIAL" (gradient dorado)
- "Precio normal: 24.99 USD" (tachado)
- **Precio:** "**9.99 USD**" (88px, gigante)
- Badge "🔥 60% DE DESCUENTO"
- **CTA dorado** con pulseGlow + shimmer: "¡SÍ, QUIERO EL COMBO AHORA!"
- 5 trust signals centrados (✓ Acceso inmediato, digital, +2 bonos, de por vida, garantía)

### 5. FAQ (líneas 1375-1410)

- **H2:** "Preguntas frecuentes"
- 4 detalles `<details>`:
  1. ¿Qué tipo de beneficios puedo esperar al usar este combo?
  2. ¿El combo tiene garantía?
  3. ¿Cómo puedo comprar y qué formas de pago aceptan?
  4. ¿Cómo recibiré los libros?

### 6. Testimonios (líneas 1412-1465)

- **H2:** "QUÉ DICEN DE NOSOTROS"
- **4 testimonial cards** rediseñadas con:
  - Borde superior gradient verde
  - Comilla decorativa grande
  - Estrellas (16px, color amarillo)
  - Headline + quote con border-left verde
  - Avatar (46px) con sombra
  - Verified badge
  - Result tag como pill gradient verde
- Testimonios: Carolina, Alejandra, Sofía, María Fernanda

### 7. Garantía (líneas 1467-1488)

- **H3:** "POLÍTICA DE GARANTÍA Y SATISFACCIÓN"
- Icono 🛡️
- 3 párrafos sobre garantía de 7 días
- Imagen del sello de garantía
- "El riesgo es TODO nuestro. El beneficio es TODO tuyo."

### 8. Footer (líneas 1490-1491)

- "© 2026 Combo Completo"
- Links: Comprar ahora, Política de privacidad, Términos

---

## 🎨 Sistema de Diseño

### Colores principales

| Color | Hex | Uso |
|-------|-----|-----|
| Verde primario | `#10b981` | CTAs, gradientes, badges |
| Verde oscuro | `#059669` | Botones, hover |
| Amarillo accent | `#f59e0b` | Badge OFERTA, precio tachado |
| Amarillo claro | `#fbbf24` | Gradiente dorado CTA |
| Naranja highlight | `#ea580c` | Gradient LLEVA GRATIS |
| Texto principal | `#0f172a` | Headings, body |
| Texto secundario | `#64748b` | Subtítulos, footer |
| Fondo claro | `#f8fafc` | Secciones alternas |
| Verde claro | `#ecfdf5` | Hero background |

### Tipografía

- **Headings:** Plus Jakarta Sans (800, 900)
- **Body:** Inter (400, 500, 600, 700)

### Animaciones

| Nombre | Uso |
|--------|-----|
| `pulse` | Pulse de elementos |
| `shine` | Efecto shine (gradient deslizante) |
| `ctaPulse` | Pulse del CTA hero |
| `pulseGlow` | Pulse del botón dorado |
| `shimmer` | Banda de luz del CTA |

### Reveal Animations

- IntersectionObserver activa `.visible` en `.reveal` cuando entran al viewport
- Threshold: 0.1
- Root margin: `0px 0px -40px 0px`

---

## 📊 Funcionalidad JavaScript

### Reveal on Scroll (líneas 1493-1506)

```javascript
(function(){
  const els=document.querySelectorAll('.reveal');
  if(!('IntersectionObserver' in window)){
    els.forEach(e=>e.classList.add('visible'));
    return;
  }
  const io=new IntersectionObserver((entries)=>{
    entries.forEach(en=>{
      if(en.isIntersecting){
        en.target.classList.add('visible');
        io.unobserve(en.target);
      }
    });
  },{threshold:0.1,rootMargin:'0px 0px -40px 0px'});
  els.forEach(e=>io.observe(e));
})();
```

### Tracking de CTAs (líneas 1508-1520)

```javascript
document.addEventListener('click',function(e){
  const a=e.target.closest('[data-track]');
  if(!a) return;
  if(typeof fbq!=='undefined'){
    fbq('trackCustom','CTA_Click',{location:a.dataset.track});
  }
  if(typeof gtag!=='undefined'){
    gtag('event','cta_click',{event_category:'CTA',event_label:a.dataset.track});
  }
});
```

---

## 🎯 CTAs de la página

| # | Ubicación | Texto | Precio asociado |
|---|-----------|-------|-----------------|
| 1 | Hero | ¡SÍ, QUIERO EL COMBO AHORA! | $9.99 USD |
| 2 | Después de productos | ¡SÍ, QUIERO EL COMBO AHORA! | $9.99 USD |
| 3 | Pricing box | 🔥 ¡SÍ, QUIERO EL COMBO AHORA! | $9.99 USD (60% off) |

---

## 📁 Estructura de Archivos

```
nutriv2-landing/
├── nutrifit/
│   ├── index.html (1538 líneas)
│   ├── icon-v2.svg
│   └── url.txt
├── .gitignore
├── CNAME (www.digibooks.online)
├── server.bat (script Windows para servidor local)
└── server.js (Node.js servidor local)
```

---

## 🚀 Deploy

- **Plataforma:** GitHub Pages
- **Custom domain:** www.digibooks.online/nutrifit/
- **DNS CNAME:** www.digibooks.online → csanchezcastillo.github.io
- **Branch:** main
- **Workflow:** Push a main → GitHub Pages build automático → CDN Fastly
- **Tiempo de deploy:** 1-2 minutos típicamente

---

## 📝 Historial de Cambios Recientes

| Commit | Descripción |
|--------|-------------|
| `0b4b797` | Price: 9.99 USD (60% off) + label 'OFERTA ESPECIAL' |
| `0cc7262` | Remove fire emoji from CTA button (kept on discount badge) |
| `9c5b8db` | Remove 'AHORRA $13.00' from discount badge |
| `e5236d4` | Price: 11.99 USD + better alignment with flex-end |
| `be1048a` | Larger product images (130->200px) + bigger fonts |
| `69eb3cd` | Increase 'EL COMBO COMPLETO INCLUYE' title font-size |
| `6566b86` | Remove CTA arrows + remove INCLUIDO labels |
| `5b3cfbe` | Fix asymmetric bonus box structure |
| `4d6f7e0` | Highlight 'LLEVA GRATIS' with orange gradient |
| `bff67f0` | Premium testimonials redesign |
| `c32c82f` | Reorder sections (FAQ first, then testimonials) |
| `3817dfd` | Premium pricing card + bonuses separated + comparison removed |

---

## 🖼️ Assets Externos (CloudFront)

| Asset | URL base |
|-------|----------|
| Combo hero image | `d1yei2z3i6k35z.cloudfront.net/15747784/6952f332f17d9_Ingles2.png` |
| Combo product image | `d1yei2z3i6k35z.cloudfront.net/11268026/68941d555e137_COMBO.png` |
| Reto Keto 21 días | `d1yei2z3i6k35z.cloudfront.net/15747784/6952ecb93e90a_689eaa4ac6d78_RetoKeto.png` |
| 30 Batidos | `d1yei2z3i6k35z.cloudfront.net/15747784/6952ec71c2e6c_689ea6e0d01ed_30Batidos.png` |
| Menús 7 Días | `d1yei2z3i6k35z.cloudfront.net/11268026/689ead3b409d7_menus7dias.png` |
| Guía Ayuno | `d1yei2z3i6k35z.cloudfront.net/11268026/689eb1611acc0_Ayunointermitente.png` |
| Audiolibro | `d1yei2z3i6k35z.cloudfront.net/11268026/689eb22137d19_AudioLibro.png` |
| Testimonios | `d1yei2z3i6k35z.cloudfront.net/11268026/...p1-p6.jpg` |
| Sello garantía | `d1yei2z3i6k35z.cloudfront.net/11268026/689ec8bd8aff3_garantia.png` |

---

## 🔧 Comandos Útiles

```bash
# Servidor local
node server.js

# Iniciar servidor en background (PowerShell)
Start-Process -FilePath "node" -ArgumentList "server.js" -WorkingDirectory "C:\Users\mqm\Desktop\Open Code\nutriv2" -PassThru -WindowStyle Hidden

# Git
git add nutrifit/index.html
git commit -m "mensaje"
git push
```

---

## 📞 Hotmart

- **URL de checkout:** `https://pay.hotmart.com/V98479276N?checkoutMode=10`
- **ID:** V98479276N
- **Modo:** 10 (one-time payment)

---

**Documento generado automáticamente.** Para actualizarlo, ejecuta el agente y pide regenerar.

<!DOCTYPE html>
<html lang="it">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Alessio Parolini - Creative Developer</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin/>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet"/>
<style>
:root {
  --c-brick-light: #ba9379;   /* Marrone chiaro dei mattoni (Sfondo 2p) */
  --c-white: #ffffff;         /* Bianco puro per titoli e accenti */
  --c-white-soft: rgba(255, 255, 255, 0.8); /* Bianco soft per i paragrafi */
  --c-yellow: #f8e123;        /* Giallo (tenuto solo per lo splash iniziale) */
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
* { font-family: 'Inter', system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif; }

html, body {
  margin: 0; padding: 0;
  background: var(--c-brick-light); 
  color: var(--c-white);
  overflow-x: hidden;
  scroll-behavior: smooth;
}

.page-wrapper {
  position: relative;
  width: 100%;
}

/* ===== SPLASH ===== */
.splash {
  position: fixed; inset: 0;
  width: 100vw; height: 100vh;
  z-index: 9999;
  pointer-events: none;
  overflow: hidden;
  animation: splashHide 0.3s ease forwards;
  animation-delay: 1.35s;
}
.splash-row { display: flex; width: 100%; height: 50%; }
.splash-box { width: 20%; height: 100%; background: var(--c-yellow); } 
.splash-row-top .splash-box { animation: splashTop 1s cubic-bezier(0.96,-0.02,0.38,1.01) forwards; }
.splash-row-bottom .splash-box { animation: splashBottom 1s cubic-bezier(0.96,-0.02,0.38,1.01) forwards; }
.splash-box:nth-child(1) { animation-delay: 0s; }
.splash-box:nth-child(2) { animation-delay: 0.05s; }
.splash-box:nth-child(3) { animation-delay: 0.1s; }
.splash-box:nth-child(4) { animation-delay: 0.15s; }
.splash-box:nth-child(5) { animation-delay: 0.2s; }

@keyframes splashTop { from { transform: translateY(0%); } to { transform: translateY(-100%); } }
@keyframes splashBottom { from { transform: translateY(0%); } to { transform: translateY(100%); } }
@keyframes splashHide { to { opacity: 0; visibility: hidden; } }

/* ===== HERO IMAGE ENTRANCE ===== */
@keyframes heroImageIn {
  from { transform: scale(1.1); opacity: 0; }
  to { transform: scale(1); opacity: 1; }
}
.hero-image-animate {
  animation: heroImageIn 1.5s cubic-bezier(0.25,0.46,0.45,0.94) forwards;
  animation-delay: 1s;
  opacity: 0;
}

/* ===== WORD REVEAL ===== */
@keyframes wordReveal {
  from { opacity: 0; transform: translateY(10px); filter: blur(10px); }
  to { opacity: 1; transform: translateY(0); filter: blur(0); }
}
.word-reveal {
  opacity: 0;
  display: inline-block;
  margin-right: 0.3em;
  animation: wordReveal 0.4s ease forwards;
}

/* ===== CREATOR TEXT ===== */
@keyframes creatorSlideUp { from { transform: translateY(150%); } to { transform: translateY(0); } }
.creator-text-animate {
  transform: translateY(150%);
  animation: creatorSlideUp 1s cubic-bezier(0.16,1,0.3,1) forwards;
  animation-delay: 1.5s;
}

/* ===== HERO (BLOCCATA SOTTO) ===== */
.hero {
  position: sticky; 
  top: 0;
  width: 100%; 
  height: 100vh; 
  overflow: hidden;
  display: flex; 
  flex-direction: column;
  justify-content: flex-end; 
  background-image: url('https://z-cdn-media.chatglm.cn/files/7807e65b-0be2-4c6a-9edf-e39c4bfdb71b.jpg?auth_key=1884739292-78f4a42244a04fef9d5aa68d7fa8cc8c-0-32a6f8017e8d48f549250902a36bf02b');
  background-size: cover;
  background-position: center 25%; 
  background-repeat: no-repeat;
  z-index: 1;
}

.hero::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(to bottom, rgba(11,11,11,0) 0%, rgba(11,11,11,0) 40%, rgba(186,147,121,0.5) 75%, rgba(186,147,121,1) 100%);
  z-index: 1;
  pointer-events: none;
}

.hero-bottom-block {
  position: relative;
  z-index: 8;
  width: 100%;
  padding: 0 40px 20px 40px; 
}

.hero-content-inner { 
  display: flex; 
  justify-content: flex-end; 
  width: 100%; 
  max-width: 1600px; 
  margin: 0 auto;
  margin-bottom: 20px; 
}

.hero-headline {
  font-size: clamp(20px, 2.2vw, 26px); 
  font-weight: 500; 
  line-height: 130%;
  letter-spacing: -0.02em; 
  color: #F4F1E8; 
  text-align: right;
  max-width: 450px;
  text-shadow: 0 4px 24px rgba(0,0,0,0.8); 
}

.hero-big-text {
  width: 100%;
  text-align: center;
  pointer-events: none;
  margin-bottom: -2%; 
}
.hero-big-text h2 {
  font-weight: 500; 
  color: #F4F1E8; 
  line-height: 80%;
  letter-spacing: -0.04em; 
  white-space: nowrap;
  font-size: clamp(120px, 22vw, 420px); 
}

/* ===== CONTENT SECTION (2p CHE COPRE) ===== */
.content-section {
  position: relative;
  z-index: 2; 
  background-image: linear-gradient(to bottom, var(--c-brick-light) 0%, #3d2818 60%, #180c05 100%);
  padding: 10vh 40px 160px 40px;
  overflow: hidden;
}

@media (min-width: 768px) {
  .content-section { padding: 10vh 80px 200px 80px; }
}

.content-inner {
  position: relative;
  max-width: 1400px; 
  margin: 0 auto;
  z-index: 2; 
}

.content-label {
  display: inline-block;
  font-size: 13px; 
  font-weight: 500;
  letter-spacing: 0.15em; 
  text-transform: uppercase;
  color: var(--c-white);
  margin-bottom: 40px;
}

.content-title {
  font-size: clamp(36px, 5.5vw, 68px);
  font-weight: 500;
  line-height: 110%;
  letter-spacing: -0.04em;
  color: var(--c-white);
  margin-bottom: 80px;
  max-width: 900px;
}
.content-title em {
  font-style: normal;
  color: var(--c-white);
}

.content-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 60px;
  margin-top: 0;
}
@media (min-width: 768px) {
  .content-grid { grid-template-columns: 1fr 1fr; gap: 120px; }
}

.content-paragraph {
  font-size: 18px; 
  font-weight: 400;
  line-height: 170%;
  color: var(--c-white-soft);
  max-width: 520px;
}

/* Stile per i "titoletti" in grassetto all'interno dei paragrafi */
.content-paragraph strong {
  display: block; /* Li mette su una nuova riga */
  color: var(--c-white);
  font-weight: 600;
  font-size: 1.2em;
  margin-top: 2em;
  margin-bottom: 0.5em;
}
.content-paragraph strong:first-child {
  margin-top: 0; /* Nessun margine per il primo titoletto del paragrafo */
}

/* Immagine Pixel Art Sempre Centrata */
.content-illustration {
  display: block;
  width: 100%;
  max-width: 450px;
  margin-top: 120px;
  margin-bottom: 0; /* Tolgo il margine sotto perché le statistiche sono state rimosse */
  margin-left: auto; 
  margin-right: auto;
}

/* ===== ANIMAZIONI REVEAL ELEGANTI ===== */
.reveal-item {
  opacity: 0;
  transform: translateY(40px);
  filter: blur(8px);
  transition: opacity 1s cubic-bezier(0.16, 1, 0.3, 1), 
              transform 1s cubic-bezier(0.16, 1, 0.3, 1), 
              filter 1s cubic-bezier(0.16, 1, 0.3, 1);
}
.reveal-item.is-visible {
  opacity: 1;
  transform: translateY(0);
  filter: blur(0);
}

/* ===== REDUCED MOTION ===== */
@media (prefers-reduced-motion: reduce) {
  .splash { animation: splashHide 0.01s linear forwards; }
  .splash-box { animation: none !important; }
  .hero-image-animate, .word-reveal, .creator-text-animate {
    animation: none !important; opacity: 1 !important;
    transform: none !important; filter: none !important; visibility: visible !important;
  }
  .reveal-item {
    opacity: 1 !important; transform: none !important; filter: none !important;
  }
}
</style>
</head>
<body>

<!-- SPLASH -->
<div class="splash" id="splash">
  <div class="splash-row splash-row-top">
    <div class="splash-box"></div><div class="splash-box"></div><div class="splash-box"></div><div class="splash-box"></div><div class="splash-box"></div>
  </div>
  <div class="splash-row splash-row-bottom">
    <div class="splash-box"></div><div class="splash-box"></div><div class="splash-box"></div><div class="splash-box"></div><div class="splash-box"></div>
  </div>
</div>

<div class="page-wrapper">
  <!-- HERO (Fissa sotto) -->
  <main class="hero hero-image-animate">
    <div class="hero-bottom-block">
      <div class="hero-content-inner">
        <h1 class="hero-headline" id="headline"></h1>
      </div>
      <div class="hero-big-text creator-text-animate">
        <h2>Alessio</h2>
      </div>
    </div>
  </main>

  <!-- SEZIONE SOTTO (2p CHE COPRE) -->
  <section class="content-section" id="about">
    <div class="content-inner">
      <span class="content-label reveal-item">ABOUT MYSELF</span>
      
      <h2 class="content-title reveal-item">
        My coding <em>journey</em>
      </h2>
      
      <div class="content-grid">
        <p class="content-paragraph reveal-item">
          <strong>I’m Alessio Parolini</strong>
          A 15-year-old student and aspiring developer based in Verona, Italy.
          
          <strong>My goals</strong>
          For over a year now, coding has been much more than just a hobby—it’s my daily passion. Every day, I put my energy into learning new concepts, building projects, and refining my technical skills, working hard to turn this into my future career.
        </p>
        
        <p class="content-paragraph reveal-item">
          <strong>My code philosophy</strong>
          I don't build software just starting from abstract ideas. Instead, I build solutions to real-world problems. To me, that’s what coding is truly all about: taking a challenge and building something practical and meaningful to solve it.
          
          <strong>Let’s connect!</strong>
          Whether you share this problem-solving mindset or have a completely different perspective, I’d love to connect, share insights, and collaborate. Feel free to reach out!
        </p>
      </div>

      <!-- IMMAGINE PIXEL ART TRASPARENTE E CENTRATA -->
      <img src="https://z-cdn-media.chatglm.cn/files/07137179-a693-403f-bd9a-01fdcd653e09.png?auth_key=1884815439-56798bcb2bf94863b25e6ab01c351fbc-0-5f64ef15d1f4d62a0d465d2f783df431" 
           alt="Programmatore al lavoro in stile pixel art" 
           class="content-illustration reveal-item"/>
    </div>
  </section>
</div>

<script>
(function() {
  // Hero Word reveal
  const headline = document.getElementById('headline');
  const text = "I don't build software from ideas. I create them from problems.";
  const words = text.split(' ');
  words.forEach(function(word, i) {
    const span = document.createElement('span');
    span.className = 'word-reveal';
    span.textContent = word;
    span.style.animationDelay = (1 + i * 0.05) + 's';
    headline.appendChild(span);
  });

  // Intersection Observer per attivare le animazioni eleganti allo scroll
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        // Aggiungi un ritardo cascata se l'elemento fa parte di un gruppo (paragrafi, statistiche)
        const siblings = Array.from(entry.target.parentElement.children);
        const index = siblings.indexOf(entry.target);
        
        // Applica un ritardo proporzionale all'indice
        entry.target.style.transitionDelay = `${index * 0.15}s`;
        entry.target.classList.add('is-visible');
        
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.15 });

  // Osserva tutti gli elementi da animare
  document.querySelectorAll('.reveal-item').forEach(el => {
    observer.observe(el);
  });
})();
</script>
</body>
</html>
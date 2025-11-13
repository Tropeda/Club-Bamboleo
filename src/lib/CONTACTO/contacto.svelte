<script>
  import { onMount } from 'svelte';
  
  // Datos de contacto - personaliza con tu información
  const contactInfo = {
    whatsapp: '+34 123 456 789',
    whatsappLink: 'https://wa.me/34123456789',
    instagram: '@bamboleo_club',
    instagramLink: 'https://instagram.com/discoteca_club',
    tiktok: '@bamboleo_club',
    tiktokLink: 'https://tiktok.com/@discoteca_club',
    direccion: 'Calle de la Fiesta, 123, 28001 Madrid'
  };

  let mounted = false;
  
  onMount(() => {
    mounted = true;
  });
</script>

<section class="contacto">

  <div class="container">
    <div class="header-section" class:visible={mounted}>
      <h2 class="neon-title">
        <span class="neon-text">CONECTA</span>
        <span class="neon-text-alt">CON NOSOTROS</span>
      </h2>
      <div class="pulse-line"></div>
    </div>
    
    <div class="contacto-grid" class:visible={mounted}>
      <!-- WhatsApp -->
      <a href={contactInfo.whatsappLink} target="_blank" rel="noopener noreferrer" class="contacto-card whatsapp">
        <div class="card-glow whatsapp-glow"></div>
        <div class="icon-wrapper">
          <div class="icon-bg"></div>
          <svg class="icon" viewBox="0 0 24 24" fill="currentColor">
            <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/>
          </svg>
        </div>
        <h3>WhatsApp</h3>
        <p class="contact-info">{contactInfo.whatsapp}</p>
        <span class="cta">
          <span class="cta-text">ENVIAR MENSAJE</span>
          <span class="arrow">→</span>
        </span>
      </a>

      <!-- Instagram -->
      <a href={contactInfo.instagramLink} target="_blank" rel="noopener noreferrer" class="contacto-card instagram">
        <div class="card-glow instagram-glow"></div>
        <div class="icon-wrapper">
          <div class="icon-bg"></div>
          <svg class="icon" viewBox="0 0 24 24" fill="currentColor">
            <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/>
          </svg>
        </div>
        <h3>Instagram</h3>
        <p class="contact-info">{contactInfo.instagram}</p>
        <span class="cta">
          <span class="cta-text">SÍGUENOS</span>
          <span class="arrow">→</span>
        </span>
      </a>

      <!-- TikTok -->
      <a href={contactInfo.tiktokLink} target="_blank" rel="noopener noreferrer" class="contacto-card tiktok">
        <div class="card-glow tiktok-glow"></div>
        <div class="icon-wrapper">
          <div class="icon-bg"></div>
          <svg class="icon" viewBox="0 0 24 24" fill="currentColor">
            <path d="M19.59 6.69a4.83 4.83 0 0 1-3.77-4.25V2h-3.45v13.67a2.89 2.89 0 0 1-5.2 1.74 2.89 2.89 0 0 1 2.31-4.64 2.93 2.93 0 0 1 .88.13V9.4a6.84 6.84 0 0 0-1-.05A6.33 6.33 0 0 0 5 20.1a6.34 6.34 0 0 0 10.86-4.43v-7a8.16 8.16 0 0 0 4.77 1.52v-3.4a4.85 4.85 0 0 1-1-.1z"/>
          </svg>
        </div>
        <h3>TikTok</h3>
        <p class="contact-info">{contactInfo.tiktok}</p>
        <span class="cta">
          <span class="cta-text">SÍGUENOS</span>
          <span class="arrow">→</span>
        </span>
      </a>

      <!-- Dirección -->
      <div class="contacto-card direccion">
        <div class="card-glow direccion-glow"></div>
        <div class="icon-wrapper">
          <div class="icon-bg"></div>
          <svg class="icon" viewBox="0 0 24 24" fill="currentColor">
            <path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z"/>
          </svg>
        </div>
        <h3>Ubicación</h3>
        <p class="contact-info">{contactInfo.direccion}</p>
        <a href={`https://maps.google.com/?q=${encodeURIComponent(contactInfo.direccion)}`} target="_blank" rel="noopener noreferrer" class="cta">
          <span class="cta-text">VER EN MAPA</span>
          <span class="arrow">→</span>
        </a>
      </div>
    </div>
  </div>
</section>

<style>
     @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Audiowide&family=Rajdhani:wght@400;500;600;700&display=swap');

  :root {
    --color-red: #dd0e0e;
    --color-red-light: #FF7070;
    --color-pink: #E89A9E;
    --color-brown: #3D2726;
    --color-gray: #808080;
    --color-white: #FFFFFF;
    --font-family-display: 'Audiowide', 'Orbitron', sans-serif;
  }
  .contacto {
    position: relative;
    padding: 120px 20px;
    background: black;
    color: white;
    overflow: hidden;
    min-height: 100vh;
    display: flex;
    align-items: center;
  }

  .background-effects {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
    z-index: 0;
  }

  .container {
    max-width: 1400px;
    margin: 0 auto;
    position: relative;
    z-index: 1;
  }

  .header-section {
    text-align: center;
    margin-bottom: 80px;
    opacity: 0;
    transform: translateY(30px);
    transition: all 1s ease;
  }

  .header-section.visible {
    opacity: 1;
    transform: translateY(0);
  }

  .neon-title {
    font-size: 3rem;
    font-weight: 900;
    margin-bottom: 30px;
    display: flex;
    flex-direction: inline-size;
    margin-left: 200px;
    gap: 10px;
    margin-top: -30px;
    font-family: var(--font-family-display);
  }

  .neon-text {
    color: #fff;
    text-shadow: 
      0 0 10px #fff,
      0 0 20px #fff,
      0 0 30px #ff00,
      0 0 40px #ff0000,
      0 0 50px #ff0000,
      0 0 60px #ff0000,
      0 0 70px #ff0000;
    animation: flicker 3s ease-in-out infinite alternate;
    letter-spacing: 5px;
  }

  .neon-text-alt {
    color: #fff;
    text-shadow: 
      0 0 10px #fff,
      0 0 20px #fff,
      0 0 30px #ff00,
      0 0 40px #ff0000,
      0 0 50px #ff0000,
      0 0 60px #ff0000,
      0 0 70px #ff0000;
    animation: flicker 3s ease-in-out infinite alternate;
    letter-spacing: 5px;
  }

  @keyframes flicker {
    0%, 80% { opacity: 1; }
    50% { opacity: 0.8; }
  }

  .pulse-line {
    width: 200px;
    height: 4px;
    margin: 0 auto;
    background: linear-gradient(90deg, 
      transparent,
      #ff0000,
      #fafafa,
      #ff0000,
      transparent
    );
    animation: pulse-line 2s ease-in-out infinite;
  }

  @keyframes pulse-line {
    0%, 100% { opacity: 0.5; transform: scaleX(0.8); }
    50% { opacity: 1; transform: scaleX(1); }
  }

  .contacto-grid {
    display: flex;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 50px;
    opacity: 0;
    transform: translateY(30px);
    transition: all 1s ease 0.3s;
  }

  .contacto-grid.visible {
    opacity: 1;
    transform: translateY(0);
  }

  .contacto-card {
    position: relative;
    background: rgba(20, 20, 20, 0.6);
    backdrop-filter: blur(20px);
    border-radius: 30px;
    padding: 50px 30px;
    text-align: center;
    text-decoration: none;
    color: white;
    display: flex;
    flex-direction: column;
    align-items: center;
    border: 2px solid rgba(255, 0, 0, 0.614);
    transition: all 0.4s ease;
    overflow: hidden;
  }

  .contacto-card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(135deg, 
      rgba(255, 255, 255, 0.1) 0%,
      transparent 50%,
      rgba(255, 255, 255, 0.1) 100%
    );
    transform: translateX(-100%);
    transition: transform 0.6s ease;
  }

  .contacto-card:hover::before {
    transform: translateX(100%);
  }

  .contacto-card:hover {
    transform: translateY(-15px) scale(1.02);
    border-color: rgba(255, 255, 255, 0.3);
  }

  .card-glow {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 100%;
    height: 100%;
    transform: translate(-50%, -50%);
    border-radius: 30px;
    opacity: 0;
    transition: opacity 0.4s ease;
    filter: blur(30px);
    z-index: -1;
  }

  .contacto-card:hover .card-glow {
    opacity: 0.6;
  }

  .whatsapp-glow {
    background: radial-gradient(circle, #25D366, transparent);
  }

  .instagram-glow {
    background: radial-gradient(circle, #E1306C, #FD1D1D, #F77737, transparent);
  }

  .tiktok-glow {
    background: radial-gradient(circle, #00f2ea, #ff0050, transparent);
  }

  .direccion-glow {
    background: radial-gradient(circle, #ffd700, #ff8c00, transparent);
  }

  .icon-wrapper {
    position: relative;
    width: 100px;
    height: 100px;
    margin-bottom: 30px;
  }

  .icon-bg {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 100%;
    height: 100%;
    transform: translate(-50%, -50%);
    border-radius: 50%;
    background: linear-gradient(135deg, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0.05));
  }

  .icon {
    position: relative;
    width: 50px;
    height: 50px;
    z-index: 2;
    transition: all 0.4s ease;
    margin-top: 25px;
  }

  .contacto-card:hover .icon {
    transform: scale(1.2) rotate(10deg);
  }

  .whatsapp .icon { color: #25D366; }
  .instagram .icon { color: #E1306C; }
  .tiktok .icon { color: #00f2ea; }
  .direccion .icon { color: #ffd700; }

  h3 {
    font-size: 2rem;
    margin-bottom: 15px;
    font-weight: 800;
    text-transform: uppercase;
    letter-spacing: 3px;
  }

  .contact-info {
    font-size: 1.2rem;
    opacity: 0.8;
    margin-bottom: 25px;
    font-weight: 300;
  }

  .cta {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    font-size: 1rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 2px;
    padding: 15px 30px;
    background: rgba(255, 255, 255, 0.1);
    border-radius: 50px;
    border: 2px solid rgba(255, 255, 255, 0.2);
    transition: all 0.3s ease;
    text-decoration: none;
    color: white;
  }

  .contacto-card:hover .cta {
    background: rgba(255, 255, 255, 0.2);
    border-color: rgba(255, 255, 255, 0.4);
    transform: scale(1.05);
  }

  .arrow {
    display: inline-block;
    transition: transform 0.3s ease;
  }

  .contacto-card:hover .arrow {
    transform: translateX(5px);
  }

  @media (max-width: 768px) {
    .contacto {
      padding: 80px 20px;
    }

    .neon-title {
      font-size: 3rem;
      margin-left: 0;
      flex-direction: column;
      align-items: center;
    }

    .contacto-grid {
      grid-template-columns: 1fr;
      gap: 30px;
      flex-direction: column;
    }

    .contacto-card {
      padding: 40px 25px;
    }

    h3 {
      font-size: 1.5rem;
    }
  }
</style>
<div class="services-grid">

  <div class="service-card">
    <div class="service-icon">
      <img src="/icons8-cóctel-32.png" alt="Icono eventos corporativos">
    </div>
    <h3 class="service-title">EVENTOS CORPORATIVOS</h3>
    <p class="service-description">Eventos corporativos de creatividad desde el concepto y el diseño, hasta la producción y gestión del evento en sí.</p>
  </div>
  
  <div class="service-card">
    <div class="service-icon">
      <img src="/icons8-micrófono-2-32.png" alt="Icono eventos de marca">
    </div>
    <h3 class="service-title">EVENTOS DE MARCA</h3>
    <p class="service-description">Nuestros eventos de marca brindan oportunidades inigualables para que usted interactúe con los clientes y haga que la marca sea aún más fuerte y reconocible.</p>
  </div>

  <div class="service-card">
    <div class="service-icon">
      <img src="/icons8-música-electrónica-32.png" alt="Icono rodajes comerciales">
    </div>
    <h3 class="service-title">RODAJES COMERCIALES</h3>
    <p class="service-description">Brindamos servicios de producción para comerciales, medios de marca, rodajes de cine/TV o documentales en muchos pabellones.</p>
  </div>

  <div class="service-card">
    <div class="service-icon">
      <img src="/icons8-bragas-32.png" alt="Icono despedidas de soltera">
    </div>
    <h3 class="service-title">DESPEDIDAS DE SOLTERA</h3>
    <p class="service-description">Crea recuerdos de despedidas de soltera que durarán toda la vida con nuestros especialistas en despedidas de soltera.</p>
  </div>

  <div class="service-card">
    <div class="service-icon">
      <img src="/icons8-fiesta-32.png" alt="Icono cumpleaños">
    </div>
    <h3 class="service-title">FIESTAS DE CUMPLEAÑOS</h3>
    <p class="service-description">Nuestros servicios de fiesta de cumpleaños incluyen DJ en vivo, baile, servicio de botella y mucho más.</p>
  </div>

  <div class="service-card">
    <div class="service-icon">
      <img src="/icons8-vip-32.png" alt="Icono VIP">
    </div>
    <h3 class="service-title">SERVICIO VIP</h3>
    <p class="service-description">Desde paquetes VIP de clubes individuales y servicios de botella hasta fiestas exclusivas cerradas.</p>
  </div>
</div>

<style>
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Audiowide&family=Rajdhani:wght@400;500;600;700&display=swap');

  :root {
    --color-red: rgb(247, 7, 7);
    --color-red-light: #FF7070;
    --color-pink: #E89A9E;
    --color-brown: #3D2726;
    --color-gray: #808080;
    --color-gray-dark: #4D4D4D;
    --font-family-main: 'Rajdhani', 'Orbitron', sans-serif;
    --font-family-display: 'Audiowide', 'Orbitron', sans-serif;
    --transition-normal: 0.3s ease;
  }

  .services-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    background-color: #000000;
    color: #fff;
    max-width: 100rem;
    margin: 0 auto;
    padding: 3rem 2rem;
    font-family: var(--font-family-main);
    gap: 0;
  }

  .service-card {
    padding: 3rem 2.5rem;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    transition: var(--transition-normal);
    border: 1px solid #2e2e2e;
    margin: -1px 0 0 -1px;
    position: relative;
    min-height: 280px;
  }

  .service-card:hover {
    background-color: rgba(247, 7, 7, 0.05);
    border-color: var(--color-red);
    z-index: 1;
  }

  .service-icon {
    width: 64px;
    height: 64px;
    margin-bottom: 1.5rem;
    display: flex;
    align-items: center;
    justify-content: center;
    filter: brightness(1.2);
    transition: var(--transition-normal);
  }

  .service-card:hover .service-icon {
    filter: brightness(1.5) drop-shadow(0 0 10px rgba(247, 7, 7, 0.5));
    transform: scale(1.1);
  }

  .service-icon img {
    width: 100%;
    height: 100%;
    object-fit: contain;
  }

  .service-title {
    font-size: 1.1rem;
    font-weight: 700;
    margin-bottom: 1rem;
    letter-spacing: 0.5px;
    color: #fff;
    font-family: var(--font-family-display);
  }

  .service-description {
    font-size: 0.95rem;
    line-height: 1.6;
    color: #ccc;
    font-family: var(--font-family-main);
  }

  /* Pantallas Extra Grandes (XL) - 1920px+ */
  @media (min-width: 1920px) {
    .services-grid {
      max-width: 120rem;
      padding: 4rem 3rem;
    }
    
    .service-card {
      padding: 4rem 3.5rem;
      min-height: 320px;
    }
    
    .service-icon {
      width: 80px;
      height: 80px;
      margin-bottom: 2rem;
    }
    
    .service-title {
      font-size: 1.3rem;
      margin-bottom: 1.25rem;
    }
    
    .service-description {
      font-size: 1.05rem;
      line-height: 1.7;
    }
  }

  /* Pantallas Grandes (L) - 1440px a 1919px */
  @media (min-width: 1440px) and (max-width: 1919px) {
    .services-grid {
      max-width: 110rem;
      padding: 3.5rem 2.5rem;
    }
    
    .service-card {
      padding: 3.5rem 3rem;
      min-height: 300px;
    }
    
    .service-icon {
      width: 72px;
      height: 72px;
      margin-bottom: 1.75rem;
    }
    
    .service-title {
      font-size: 1.2rem;
      margin-bottom: 1.15rem;
    }
    
    .service-description {
      font-size: 1rem;
      line-height: 1.65;
    }
  }

  /* Desktop Normal - 1025px a 1439px */
  @media (min-width: 1025px) and (max-width: 1439px) {
    .services-grid {
      padding: 3rem 2rem;
    }
    
    .service-card {
      padding: 3rem 2.5rem;
    }
  }

  /* Tablet - 769px a 1024px */
  @media (min-width: 769px) and (max-width: 1024px) {
    .services-grid {
      grid-template-columns: repeat(2, 1fr);
      padding: 2.5rem 2rem;
    }
    
    .service-card {
      padding: 2.5rem 2rem;
      min-height: 260px;
    }
  }

  /* Mobile - hasta 768px */
  @media (max-width: 768px) {
    .services-grid {
      grid-template-columns: 1fr;
      padding: 1.5rem 1rem;
    }
    
    .service-card {
      padding: 2rem 1.5rem;
      border: none !important;
      border-bottom: 1px solid #2e2e2e !important;
      margin: 0;
      min-height: auto;
    }
    
    .service-card:last-child {
      border-bottom: none !important;
    }

    .service-card:hover {
      background-color: transparent;
      border-color: inherit !important;
    }
    
    .service-icon {
      width: 56px;
      height: 56px;
    }
    
    .service-title {
      font-size: 1rem;
    }
    
    .service-description {
      font-size: 0.9rem;
    }
  }
</style>
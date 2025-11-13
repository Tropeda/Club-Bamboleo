<script>
  import { onMount } from 'svelte';
  
  let currentIndex = 0;
  let isAnimating = false;
  
  const items = [
    {
      id: 1,
      number: '05',
      season: 'AGOSTO',
      title: 'NOCHE ELÉCTRICA',
      date: 'La música vibraba en el aire, una mezcla pegadiza de ritmos latinos y éxitos pop que invitaba a todos a moverse; las luces de colores giraban frenéticamente, pintando rostros sonrientes y copas alzadas en el ambiente cargado de una energía contagiosa.',
      image: 'evento1.jpg'
    },
    {
      id: 2,
      number: '12',
      season: 'ENERO',
      title: 'REGGATON SUNSET',
      date: 'La música vibraba en el aire, una mezcla pegadiza de ritmos latinos y éxitos pop que invitaba a todos a moverse; las luces de colores giraban frenéticamente, pintando rostros sonrientes y copas alzadas en el ambiente cargado de una energía contagiosa.',
      image: 'evento2.jpg'
    },
    {
      id: 3,
      number: '23',
      season: 'FEBRERO',
      title: 'JUEVES UNIVERSITARIO',
      date: 'La música vibraba en el aire, una mezcla pegadiza de ritmos latinos y éxitos pop que invitaba a todos a moverse; las luces de colores giraban frenéticamente, pintando rostros sonrientes y copas alzadas en el ambiente cargado de una energía contagiosa.',
      image: 'evento3.jpg'
    },
    {
      id: 4,
      number: '18',
      season: 'MARZO',
      title: 'FLAMENCO NIGHT',
      date: 'La música vibraba en el aire, una mezcla pegadiza de ritmos latinos y éxitos pop que invitaba a todos a moverse; las luces de colores giraban frenéticamente, pintando rostros sonrientes y copas alzadas en el ambiente cargado de una energía contagiosa.',
      image: 'evento4.jpg'
    },
    {
      id: 5,
      number: '25',
      season: 'FEBRERO',
      title: 'VERDIALES TECNO',
      date: 'La música vibraba en el aire, una mezcla pegadiza de ritmos latinos y éxitos pop que invitaba a todos a moverse; las luces de colores giraban frenéticamente, pintando rostros sonrientes y copas alzadas en el ambiente cargado de una energía contagiosa.',
      image: 'evento5.jpg'
    }
  ];
  
  function nextSlide() {
    if (isAnimating) return;
    isAnimating = true;
    currentIndex = (currentIndex + 1) % items.length;
    setTimeout(() => isAnimating = false, 500);
  }
  
  function prevSlide() {
    if (isAnimating) return;
    isAnimating = true;
    currentIndex = (currentIndex - 1 + items.length) % items.length;
    setTimeout(() => isAnimating = false, 500);
  }
  
  function getVisibleItems() {
    const visible = [];
    for (let i = -1; i <= 1; i++) {
      const index = (currentIndex + i + items.length) % items.length;
      visible.push({ ...items[index], position: i });
    }
    return visible;
  }
  
  onMount(() => {
    const interval = setInterval(() => {
      nextSlide();
    }, 5000);
    
    return () => clearInterval(interval);
  });
</script>

<div class="container">
  <!-- Background -->
  <div class="background"></div>
  
  <!-- Content -->
  <div class="content">
    <div class="title-wrapper">
      <h1 class="title">
        <span class="letter">P</span>
        <span class="letter">R</span>
        <span class="letter">Ó</span>
        <span class="letter">X</span>
        <span class="letter">I</span>
        <span class="letter">M</span>
        <span class="letter">O</span>
        <span class="letter">S</span>
        <span class="letter space"></span>
        <span class="letter">E</span>
        <span class="letter">V</span>
        <span class="letter">E</span>
        <span class="letter">N</span>
        <span class="letter">T</span>
        <span class="letter">O</span>
        <span class="letter">S</span>
      </h1>
      <div class="title-glow"></div>
    </div>
    
    <div class="carousel-wrapper">
      <!-- Navigation Button Left -->
      <button class="nav-button left" on:click={prevSlide} aria-label="Previous">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M15 18l-6-6 6-6"/>
        </svg>
      </button>
      
      <!-- Carousel -->
      <div class="carousel">
        {#each getVisibleItems() as item (item.id)}
          <div 
            class="card {item.position === 0 ? 'active' : ''} {item.position === -1 ? 'prev' : ''} {item.position === 1 ? 'next' : ''}"
            style="--position: {item.position}"
          >
            <div class="card-inner">
              <div class="season-badge">
                <span class="season-number">{item.number}</span>
                <span class="season-text">{item.season}</span>
              </div>
              
              <div class="card-image">
                <img src={item.image} alt={item.title} />
              </div>
              
              <div class="card-content">
                <h3 class="card-title">{item.title}</h3>
                <p class="card-date">{item.date}</p>
                <div class="progress-container">
                  <div class="progress-bar"></div>
                </div>
              </div>
            </div>
          </div>
        {/each}
      </div>
      
      <!-- Navigation Button Right -->
      <button class="nav-button right" on:click={nextSlide} aria-label="Next">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M9 18l6-6-6-6"/>
        </svg>
      </button>
    </div>
    
    <!-- Indicators -->
    <div class="indicators">
      {#each items as item, index}
        <button 
          class="indicator {index === currentIndex ? 'active' : ''}"
          on:click={() => { currentIndex = index; }}
          aria-label="Go to slide {index + 1}"
        ></button>
      {/each}
    </div>
  </div>
</div>

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

  :global(body) {
    margin: 0;
    padding: 0;
    font-family: 'Rajdhani', 'Orbitron', sans-serif;
    overflow-x: hidden;
  }

  .container {
    position: relative;
    min-height: 100vh;
    color: var(--color-red, rgb(229, 225, 225));
    overflow: hidden;
  }

  .background {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-image: url('fondo-videos.png');
    background-size: cover;        
    background-repeat: no-repeat;    
    background-position: 30% 30%; 
    transition: background-position 0.3s ease;
    z-index: 0;
  }

  .content {
    position: relative;
    z-index: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    padding: 40px 20px;
  }

  .title-wrapper {
    position: relative;
    margin-bottom: 60px;
    perspective: 1000px;
  }

  .title {
    font-size: 3rem;
    font-weight: 900;
    font-family: 'Audiowide', 'Orbitron', sans-serif;
    letter-spacing: 0.2em;
    text-align: center;
    margin: 0;
    position: relative;
    z-index: 2;
  }

  .letter {
    display: inline-block;
    background: red;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    text-shadow: 0 0 30px rgba(241, 146, 151, 0.6);
    filter: drop-shadow(0 0 20px rgba(232, 154, 158, 0.4));
    transform-origin: center;
    background-size: 200% 200%;
  }


  .letter:hover {
    animation: bounce 0.6s ease, shimmer 4s linear infinite;
    transform: scale(1.3) rotate(5deg);
  }

  .title-glow {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 120%;
    height: 150%;
    animation: pulse-glow 3s ease-in-out infinite;
    z-index: 1;
    pointer-events: none;
    filter: blur(20px);
  }


  .carousel-wrapper {
    position: relative;
    display: flex;
    align-items: center;
    gap: 0px;
    margin-bottom: 50px;
    
  }

  .carousel {
    position: relative;
    width: 1000px;
    height: 500px;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .card {
    position: absolute;
    width: 300px;
    height: 420px;
    transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
    cursor: pointer;
  }

  .card.prev {
    transform: translateX(-300px) scale(0.85);
    opacity: 0.5;
    z-index: 1;
  }

  .card.active {
    transform: translateX(0) scale(1);
    opacity: 1;
    z-index: 2;
  }

  .card.next {
    transform: translateX(300px) scale(0.85);
    opacity: 0.5;
    z-index: 1;
  }

  .card-inner {
    width: 100%;
    height: 120%;
    background: linear-gradient(135deg, #3D2726 0%, #4D4D4D 100%);
    border-radius: 20px;
    overflow: hidden;
    position: relative;
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.6);
    transition: transform 0.3s ease;
  }

  .card.active .card-inner:hover {
    transform: translateY(-10px);
  }

  .season-badge {
    position: absolute;
    top: 15px;
    left: 15px;
    z-index: 3;
    display: flex;
    flex-direction: column;
    align-items: center;
    background: rgba(0, 0, 0, 0.5);
    backdrop-filter: blur(10px);
    padding: 8px 12px;
    border-radius: 10px;
    border: 1px solid rgba(255, 255, 255, 0.1);
  }

  .season-number {
    font-size: 1.5rem;
    font-weight: 900;
    font-family: 'Audiowide', 'Orbitron', sans-serif;
  }

  .season-text {
    font-size: 0.6rem;
    font-weight: 600;
    font-family: 'Rajdhani', sans-serif;
    letter-spacing: 0.1em;
    opacity: 0.8;
  }

  .card-image {
    width: 100%;
    height: 280px;
    overflow: hidden;
  }

  .card-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.5s ease;
  }

  .card.active .card-inner:hover .card-image img {
    transform: scale(1.1);
  }

  .card-content {
    padding: 20px;
  }

  .card-title {
    font-size: 1.2rem;
    font-weight: 900;
    font-family: 'Audiowide', 'Orbitron', sans-serif;
    letter-spacing: 0.05em;
    margin: 0 0 8px 0;
    text-transform: uppercase;
  }

  .card-date {
    font-size: 0.8rem;
    font-family: 'Rajdhani', sans-serif;
    color: #E89A9E;
    margin-bottom: 15px;
    letter-spacing: 0.1em;
  }


  @keyframes pulse {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.7; }
  }

  .nav-button {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    background: rgba(232, 154, 158, 0.2);
    backdrop-filter: blur(10px);
    border: 1px solid #E89A9E;
    color: #fff;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.3s ease;
    z-index: 10;
    margin-left: -40px;
    margin-right: -40px;
  }

  .nav-button:hover {
    background: rgba(232, 154, 158, 0.4);
    border-color: #FF7070;
    transform: scale(1.1);
  }

  .indicators {
    display: flex;
    gap: 12px;
    margin-top: 20px;
  }

  .indicator {
    width: 10px;
    height: 10px;
    border-radius: 50%;
    background: rgba(232, 154, 158, 0.5);
    border: none;
    cursor: pointer;
    transition: all 0.3s ease;
  }

  .indicator.active {
    background: var(--color-red);
    width: 30px;
    border-radius: 5px;
  }

  @media (max-width: 768px) {
    .title {
      font-size: 2rem;
    }
    .carousel {
      width: 280px;
      height: 450px;
    }
    .card {
      width: 240px;
      height: 360px;
    }
    .nav-button {
      width: 40px;
      height: 40px;
    }
  }
</style>
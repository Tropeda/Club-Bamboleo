<script>
  import TextPressure from './TextPressure.svelte';
  
  /**
   * @type {{ update: (arg0: (val: any) => boolean) => void; }}
   */
   export let isPlaying;
  
  let showPlayButton = true;
  let showPlayer = false;
  let spotifyKey = 0; // Para forzar recreación del iframe

  function togglePlay() {
    isPlaying.update(val => !val);
    showPlayer = !showPlayer;
    
    if (!showPlayer) {
      showPlayer = false;
    } else {
      spotifyKey++;
    }
  }

  // Reacciona a cambios en isPlaying
  $: if ($isPlaying) {
    showPlayer = true;
    spotifyKey++; // Forzar recreación del iframe
  } else {
    showPlayer = false;
  }

  // Función para scroll suave hacia arriba
  function scrollToTop() {
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }
</script>

<section class="hero">
  <div class="hero-background">
    <img src="/front.avif" alt="ADN Club" class="background-image" />
    <div class="overlay"></div>
  </div>

  <div class="hero-content">
    <div class="hero-text">
      <TextPressure text="BAMBOLEO" />
      <TextPressure text="CLUB" className="subtitle" />
    </div>

    <div class="center">
      {#if showPlayer}
        {#key spotifyKey}
        <div class="spotify-player">
          <iframe 
            style="border-radius:12px" 
            src="https://open.spotify.com/embed/playlist/2pFMiJvbP91UIO31eYRTLS?utm_source=generator&autoplay=1" 
            width="100%" 
            height="152" 
            frameBorder="0" 
            allowfullscreen="" 
            allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" 
            title="Spotify Player">
          </iframe>
        </div>
        {/key}
      {:else if showPlayButton}
        <button 
          class="play-button" 
          on:click={togglePlay} 
          class:playing={$isPlaying}
          title={$isPlaying ? 'Pausar música' : 'Reproducir música'}
        >
          <svg viewBox="0 0 100 100" fill="currentColor">
            {#if $isPlaying}
              <rect x="25" y="20" width="15" height="60" />
              <rect x="60" y="20" width="15" height="60" />
            {:else}
              <polygon points="30,20 80,50 30,80" />
            {/if}
          </svg>
        </button>
      {/if}
    </div>
  </div>

  <!-- Flecha fija para volver arriba -->
  <button class="back-to-top" on:click={scrollToTop} title="Volver arriba">↑</button>
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

  .hero {
    position: relative;
    width: 100vw;
    height: 110vh;
    overflow: hidden;
    margin: -8px;
    padding: 0;
  }

  .hero-background {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
  }

.background-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    margin-top: 100px;
    filter: brightness(0.3); 
}

  .overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(
      135deg,
      rgba(255, 51, 51, 0.3) 0%,
      rgba(77, 77, 77, 0.4) 10%,
      rgba(61, 39, 38, 0.3) 50%
    );
    z-index: 2;
  }

  .hero-content {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    z-index: 3;
  }

  .hero-text {
    text-align: center;
    margin-bottom: 40px;
    animation: fadeInDown 1s ease-out;
    margin-top: 150px;
  }

  .subtitle {
    font-family: var(--font-family-display);
    font-size: clamp(32px, 8vw, 80px);
    font-weight: 400;
    color: var(--color-red);
    margin: 20px 0 0 0;
    padding: 0;
    text-shadow: 0 0 20px rgba(255, 51, 51, 0.9),
                 0 0 40px rgba(255, 51, 51, 0.6);
    letter-spacing: 2px;
    font-style: italic;
  }

  .play-button {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    border: 3px solid var(--color-red);
    background: transparent;
    color: red;
    display: flex;
    align-items: center;
    justify-content: left;
    cursor: pointer;
    transition: all 0.3s ease;
    margin-bottom: 40px;
    position: relative;
    z-index: 4;
    animation: fadeInUp 1s ease-out 0.2s both;
  }

  .play-button:hover {
    box-shadow: 0 0 30px rgba(255, 51, 51, 0.8),
                inset 0 0 30px rgba(255, 51, 51, 0.4);
    transform: scale(1.1);
  }

  .play-button:active {
    transform: scale(0.95);
  }

.play-button svg {
    width: 50px;
    height: 50px;
    stroke: red; 
    stroke-width: 3px;
    fill: none;
    margin-left: 18px;
    filter: drop-shadow(0 0 8px #ff6666); 
}

  .play-button.playing {
    animation: pulsing 1s ease-in-out infinite;
  }

  .spotify-player {
    padding: 1px;
    border-radius: 15px;
    outline: 1px solid black;
    max-width:25rem;
    pointer-events: auto;
    animation: fadeInUp 0.5s ease-out;
  }

  /* Flecha back-to-top */
  .back-to-top {
    position: fixed;
    bottom: 30px;
    right: 30px;
    background-color: var(--color-red);
    color: var(--color-white);
    font-size: 1.6rem;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    text-decoration: none;
    z-index: 10;
    box-shadow: 0px 0px 30px var(--color-red);
    cursor: pointer;
    transition: all 0.3s ease;
  }

  .back-to-top:hover {
    background-color: var(--color-red-light);
    transform: translateY(-5px);
  }

  @keyframes fadeInDown {
    from { opacity: 0; transform: translateY(-30px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes fadeInUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes pulsing {
    0%, 100% {
      box-shadow: 0 0 20px rgba(255, 51, 51, 0.5),
                  inset 0 0 20px rgba(255, 51, 51, 0.2);
    }
    50% {
      box-shadow: 0 0 40px rgba(255, 51, 51, 0.8),
                  inset 0 0 40px rgba(255, 51, 51, 0.4);
    }
  }

  @media (max-width: 768px) {
    .subtitle {
      font-size: clamp(24px, 6vw, 40px);
    }
    .play-button { width: 80px; height: 80px; }
    .play-button svg { width: 40px; height: 40px; }
    .spotify-player { bottom: 10px; padding: 10px; }
  }

  @media (max-width: 480px) {
    .subtitle { font-size: clamp(18px, 5vw, 28px); }
    .play-button { width: 60px; height: 60px; margin-bottom: 20px; }
    .play-button svg { width: 30px; height: 30px; }
    .hero-text { margin-bottom: 20px; }
  }
</style>

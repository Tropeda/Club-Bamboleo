<script>
  import TextPressure from './TextPressure.svelte';
  export let isPlaying;

  let showPlayButton = true;
  let showPlayer = false;
  let spotifyKey = 0;

  function togglePlay() {
    isPlaying.update(val => !val);
    showPlayer = !showPlayer;
    if (showPlayer) spotifyKey++;
  }

  $: if ($isPlaying) {
    showPlayer = true;
    spotifyKey++;
  } else {
    showPlayer = false;
  }

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
              height="100%"
              frameBorder="0"
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
        >
          <svg viewBox="0 0 100 100">
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

  <button class="back-to-top" on:click={scrollToTop}>↑</button>
</section>

<style>
  :root {
    --red: #dd0e0e;
    --white: #fff;
    --font-display: 'Audiowide', 'Orbitron', sans-serif;
  }

  .hero {
    position: relative;
    width: 100%;
    height: 100svh;
    overflow: hidden;
  }

  .hero-background {
    position: absolute;
    inset: 0;
    z-index: 1;
  }

  .background-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    filter: brightness(0.3);
  }

  .overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(
      135deg,
      rgba(255, 51, 51, 0.3),
      rgba(77, 77, 77, 0.4),
      rgba(61, 39, 38, 0.3)
    );
    z-index: 2;
  }

  .hero-content {
    position: relative;
    z-index: 3;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 1rem;
    text-align: center;
  }

  .hero-text {
    margin-bottom: 1rem;
    margin-top: 3rem;
    width: 100%;
    text-align: center;
  }

  .hero-text :global(.text-pressure) {
    display: inline-block;
    max-width: 100%;
  }

  .subtitle {
    font-family: var(--font-display);
    font-size: clamp(32px, 8vw, 80px);
    color: var(--red);
    text-shadow: 0 0 20px rgba(255, 51, 51, 0.9);
  }

  .center {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: auto;
  }

  .play-button {
    width: clamp(70px, 15vw, 110px);
    height: clamp(70px, 15vw, 110px);
    border-radius: 50%;
    border: 3px solid var(--red);
    background: transparent;
    cursor: pointer;
    transition: .3s;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .play-button svg {
    width: 60%;
    height: 60%;
    fill: var(--red);
  }

  .spotify-player {
    width: min(90vw, 420px);
    aspect-ratio: 2.6 / 1;
    position: relative;
    display: flex;
  }

  .spotify-player iframe {
    position: absolute;
    width: 100%;
    height: 100%;
  }

  .back-to-top {
    position: fixed;
    bottom: 2rem;
    right: 2rem;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    background: var(--red);
    color: var(--white);
    font-size: 1.8rem;
    border: none;
    box-shadow: 0 0 15px var(--red);
    cursor: pointer;
    z-index: 10;
  }

  /* Media queries simplificados, sin márgenes locos para centrar */
  @media (max-width: 768px) {
    .hero-text { margin-top: 2rem; }
    .spotify-player { width: 90vw; }
  }

  @media (max-width: 425px) {
    .hero-text { margin-top: 1rem; }
    .spotify-player { width: 92vw; }
    .play-button { width: 65px; height: 65px; }
  }

  @media (max-width: 375px) {
    .hero-text { margin-top: 0.5rem; }
    .spotify-player { width: 95vw; }
  }

  @media (max-width: 320px) {
    .hero { min-height: 100dvh; }
    .spotify-player { width: 95vw; }
  }
</style>

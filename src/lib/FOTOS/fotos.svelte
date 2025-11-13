<script>
  // Array de imágenes - reemplaza con tus URLs
  let images = [
    { src: 'dj.avif', alt: 'DJ en evento' },
    { src: 'fiesta-nocturna.avif', alt: 'Fiesta nocturna' },
    { src: 'bartender.avif', alt: 'Bartender' },
    { src: 'amigos.avif', alt: 'Amigas' },
    { src: 'bailarina.avif', alt: 'Bailarina' },
    { src: 'baile.avif', alt: 'Baile' },
    { src: 'grupo.avif', alt: 'Grupo de amigos' },
    { src: 'dj2.avif', alt: 'DJ profesional' }
  ];

  let selectedImage = null;

  function openLightbox(img) {
    selectedImage = img;
  }

  function closeLightbox() {
    selectedImage = null;
  }
</script>

<div class="gallery-container">
  <div class="gallery-header">
    <h1 class="gallery-title">PHOTOCALL</h1>
  </div>
  
  <div class="photo-grid">
    {#each images as img, i}
      <div class="photo-item photo-item-{i + 1}" on:click={() => openLightbox(img)} on:keydown={(e) => e.key === 'Enter' && openLightbox(img)} role="button" tabindex="0">
        <img src={img.src} alt={img.alt} />
        <div class="overlay">
          <span class="view-text">Ver imagen</span>
        </div>
      </div>
    {/each}
  </div>
</div>

{#if selectedImage}
  <div class="lightbox" on:click={closeLightbox} on:keydown={(e) => e.key === 'Escape' && closeLightbox()} role="button" tabindex="0">
    <button class="close-btn" on:click={closeLightbox}>&times;</button>
    <img src={selectedImage.src} alt={selectedImage.alt} class="lightbox-image" />
  </div>
{/if}

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
  .gallery-container {
    max-width: 1950px;
    margin: 0 auto;
    padding: 2rem;
    background: black;
    min-height: 100vh;
  }

  .gallery-header {
    text-align: center;
    margin-bottom: 3rem;
  }

  .gallery-title {
    font-size: 3.5rem;
    font-weight: 700;
    color: var(--color-red);
    text-transform: uppercase;
    letter-spacing: 0.8rem;
    background: linear-gradient(40deg, #fcfcfc, #dd0e0e, #dd0e0e);
    background-size: 200% auto;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    animation: gradient 3s ease infinite;
    font-family: var(--font-family-display);
    text-shadow: 0 0 30px rgba(103, 15, 15, 0.5);
    margin-top: -30px;
  }

  @keyframes gradient {
    0%, 100% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
  }

  .photo-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(3, 250px);
    gap: 1rem;
    grid-auto-flow: dense;
  }

  .photo-item {
    position: relative;
    overflow: hidden;
    border-radius: 12px;
    cursor: pointer;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }

  .photo-item:hover {
    transform: scale(1.05);
    box-shadow: 0 10px 30px var(--color-red);
    z-index: 10;
  }

  /* Layout específico para crear el collage */
  .photo-item-1 {
    grid-column: 1;
    grid-row: 1;
  }

  .photo-item-2 {
    grid-column: 2;
    grid-row: 1;
  }

  .photo-item-3 {
    grid-column: 3;
    grid-row: 1 / 3;
  }

  .photo-item-4 {
    grid-column: 4;
    grid-row: 1;
  }

  .photo-item-5 {
    grid-column: 1;
    grid-row: 2 / 4;
  }

  .photo-item-6 {
    grid-column: 2;
    grid-row: 2;
  }

  .photo-item-7 {
    grid-column: 2 / 4;
    grid-row: 3;
  }

  .photo-item-8 {
    grid-column: 4;
    grid-row: 2 / 4;
  }

  .photo-item img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
    transition: transform 0.3s ease;
  }

  .photo-item:hover img {
    transform: scale(1.1);
  }

  .overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.7);
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0;
    transition: opacity 0.3s ease;
  }

  .photo-item:hover .overlay {
    opacity: 1;
  }

  .view-text {
    color: var(--color-white);
    font-size: 1.1rem;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.1rem;
    font-family: var(--font-family-display);
  }

  .lightbox {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.95);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1000;
    cursor: pointer;
  }

  .lightbox-image {
    max-width: 90%;
    max-height: 90%;
    object-fit: contain;
    border-radius: 8px;
  }

  .close-btn {
    position: absolute;
    top: 2rem;
    right: 2rem;
    background: transparent;
    border: none;
    color: #fff;
    font-size: 3rem;
    cursor: pointer;
    transition: transform 0.2s ease;
    z-index: 1001;
  }

  .close-btn:hover {
    transform: scale(1.2);
    color: var(--color-red);
  }

  @media (max-width: 1024px) {
    .photo-grid {
      grid-template-columns: repeat(3, 1fr);
      grid-template-rows: repeat(4, 200px);
    }

    .photo-item-1, .photo-item-2, .photo-item-4, .photo-item-6 {
      grid-column: auto;
      grid-row: auto;
    }

    .photo-item-3 {
      grid-column: 3;
      grid-row: 1 / 3;
    }

    .photo-item-5 {
      grid-column: 1;
      grid-row: 2 / 4;
    }

    .photo-item-7 {
      grid-column: 2 / 4;
      grid-row: 4;
    }

    .photo-item-8 {
      grid-column: 3;
      grid-row: 3 / 5;
    }
  }

  @media (max-width: 768px) {
    .gallery-title {
      font-size: 2rem;
    }

    .photo-grid {
      grid-template-columns: repeat(2, 1fr);
      grid-template-rows: repeat(6, 180px);
    }

    .photo-item-1, .photo-item-2, .photo-item-3, 
    .photo-item-4, .photo-item-5, .photo-item-6,
    .photo-item-7, .photo-item-8 {
      grid-column: auto;
      grid-row: auto;
    }
  }

  @media (max-width: 480px) {
    .gallery-container {
      padding: 1rem;
    }

    .photo-grid {
      grid-template-columns: 1fr;
      grid-template-rows: repeat(8, 250px);
    }
  }
</style>
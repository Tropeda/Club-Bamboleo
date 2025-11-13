<script>
  let currentIndex = 0;
  let videoElement;

  let videos = [
    {
      id: 1,
      thumbnail: '/foto-video1.jpg',
      videoUrl: '/video1.mp4',
      title: 'VIERNES MORUNO'
    },
    {
      id: 2,
      thumbnail: '/foto-video2.jpg',
      videoUrl: '/video2.mp4',
      title: 'SÁBADO RUMBERO'
    },
    {
      id: 3,
      thumbnail: '/foto-video3.jpeg',
      videoUrl: '/video3.mp4',
      title: 'DOMINGO DE BAMBOLEO'
    }
  ];

  let isPlaying = false;

  async function handlePlayClick() {
    isPlaying = true;
    await new Promise(resolve => setTimeout(resolve, 100));
    if (videoElement) {
      try {
        await videoElement.play();
      } catch (error) {
        console.error('Error al reproducir:', error);
        isPlaying = false;
      }
    }
  }

  // Click en el video -> pausa o reanuda
  function handleVideoClick() {
    if (!videoElement) return;
    if (videoElement.paused) {
      videoElement.play();
    } else {
      videoElement.pause();
    }
  }

  function handleVideoPause() {
    isPlaying = false;
  }

  function handleVideoPlay() {
    isPlaying = true;
  }

  function handleVideoEnd() {
    isPlaying = false;
  }

  function nextVideo() {
    if (videoElement) {
      videoElement.pause();
      videoElement.currentTime = 0;
    }
    isPlaying = false;
    currentIndex = (currentIndex + 1) % videos.length;
    if (videoElement) videoElement.load();
  }

  function prevVideo() {
    if (videoElement) {
      videoElement.pause();
      videoElement.currentTime = 0;
    }
    isPlaying = false;
    currentIndex = (currentIndex - 1 + videos.length) % videos.length;
    if (videoElement) videoElement.load();
  }
</script>

<section class="video-slider">
  <div class="video-container">
    <div class="video-wrapper">
      {#if !isPlaying}
        <div
          class="video-thumbnail"
          style="background-image: url('{videos[currentIndex].thumbnail}')"
        >
          <button class="play-button" on:click={handlePlayClick} aria-label="Reproducir video">
            ▶
          </button>
          <div class="video-title">{videos[currentIndex].title}</div>
        </div>
      {/if}

      <!-- Video -->
      <!-- svelte-ignore a11y_media_has_caption -->
      <video
        bind:this={videoElement}
        class="video-player"
        on:ended={handleVideoEnd}
        on:pause={handleVideoPause}
        on:play={handleVideoPlay}
        on:click={handleVideoClick}
        preload="auto"
      >
        <source src={videos[currentIndex].videoUrl} type="video/mp4" />
      </video>
    </div>

    <!-- Botones de navegación SIEMPRE visibles -->
    <button class="nav-button prev" on:click={prevVideo} aria-label="Video anterior">❮</button>
    <button class="nav-button next" on:click={nextVideo} aria-label="Siguiente video">❯</button>
  </div>
</section>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Audiowide&display=swap');

  :root {
    --color-red: #d01a1a;
    --color-white: #fff;
  }

  .video-slider {
    width: 100%;
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background-image: url('/fondo-videos.png');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
  }

  .video-container {
    position: relative;
    width: 80%;
    max-width: 1000px;
    aspect-ratio: 16 / 9;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: rgb(196, 38, 38) 0 0 40px;
  }

  .video-wrapper {
    width: 100%;
    height: 100%;
    position: relative;
    background: #000;
  }

  .video-thumbnail {
    position: absolute;
    inset: 0;
    background-size: cover;
    background-position: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    z-index: 3;
  }

  .video-title {
    position: absolute;
    bottom: 20px;
    left: 0;
    right: 0;
    text-align: center;
    font-family: 'Audiowide', sans-serif;
    font-size: 22px;
    color: rgb(196, 38, 38);
    text-shadow: 0 0 10px rgba(0, 0, 0, 0.7);
  }

  .play-button {
    font-size: 45px;
    background: transparent;
    color: rgb(196, 38, 38);
    border: 2.5px solid rgb(196, 38, 38);
    border-radius: 20%;
    padding: 15px;
    cursor: pointer;
    transition: transform 0.3s ease;
    z-index: 4;
    text-shadow: #000 0 5px 20px;
  }

  .play-button:hover {
    transform: scale(1.2);
  }

  .video-player {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: 2;
    background: #000;
    cursor: pointer;
  }

  /* ✅ Flechas SIEMPRE visibles y por encima del video */
  .nav-button {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background: transparent;
    color: rgb(196, 38, 38);
    font-size: 25px;
    padding: 10px 20px;
    cursor: pointer;
    transition: all 0.3s ease;
    z-index: 5;
    border-radius: 10%;
    margin-left: -15px;
    margin-right: -15px;
  }

  .nav-button:hover {
    background: rgba(6, 4, 4, 0.2);
    transform: translateY(-50%) scale(1.1);
  }

  .nav-button.prev {
    left: 10px;
  }

  .nav-button.next {
    right: 10px;
  }

  @media (max-width: 768px) {
    .nav-button {
      font-size: 30px;
      padding: 8px 15px;
    }
    .play-button {
      font-size: 35px;
      padding: 10px;
    }
  }
</style>

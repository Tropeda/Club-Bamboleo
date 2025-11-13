<script>
  import { onMount } from 'svelte';
  
  let inView = false;
  let sectionRef;
  
  const title = "SOBRE BAMBOLEO";
  const letters = title.split('');
  
  onMount(() => {
    const observer = new IntersectionObserver(
      ([entry]) => {
        if (entry.isIntersecting) {
          inView = true;
          observer.unobserve(sectionRef);
        }
      },
      { threshold: 0.1, rootMargin: '0px' }
    );
    
    observer.observe(sectionRef);
    
    return () => observer.disconnect();
  });
</script>

<section class="about-section" bind:this={sectionRef}>
  <div class="about-background">
    <img src="/about.avif" alt="About Club" class="background-image" />
    <div class="overlay"></div>
  </div>

  <div class="about-content">
    <h2 class="about-title">
      {#each letters as letter, index}
        <span 
          class="letter" 
          class:animate={inView}
          style="animation-delay: {index * 0.05}s;"
        >
          {letter === ' ' ? '\u00A0' : letter}
        </span>
      {/each}
    </h2>
    <p class="about-text">
      El espíritu de nuestro club nocturno es inigualable. Desde el momento en que entras, te sumerges en un mundo de música, luces y vibraciones inolvidables. Nuestros eventos reúnen a los DJ y artistas más talentosos, creando una atmósfera que hace que todos quieran volver por más. Únete a nosotros y vive la mejor aventura nocturna.
    </p>
  </div>
</section>

<style>
  .about-section {
    position: relative;
    width: 100%;
    max-width: 100vw;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    color: var(--color-white);
    font-family: 'Rajdhani', 'Audiowide', sans-serif;
    overflow: hidden;
  }

  .about-background {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
    overflow: hidden;
  }

  .background-image {
    position: absolute;
    top: 0;
    left: 0;
    width: 100vw; 
    height: 100%;
    object-fit: cover;
    filter: brightness(0.5);
    max-width: 100%;
  }

  .overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(
      135deg,
      rgba(255, 51, 51, 0.3) 0%,
      rgba(77, 77, 77, 0.4) 10%,
      rgba(61, 39, 38, 0.3) 50%
    );
    z-index: 2;
  }

  .about-content {
    position: relative;
    z-index: 3;
    max-width: 900px;
  }

  .about-title {
    font-family: var(--font-family-display);
    font-size: clamp(32px, 6vw, 64px);
    font-weight: 900;
    color: white;
    margin-bottom: 20px;
    text-shadow: 0 0 20px rgba(255, 51, 51, 0.9),
                 0 0 40px rgba(255, 51, 51, 0.6);
    display: inline-block;
  }

  .letter {
    display: inline-block;
    opacity: 0;
    filter: blur(10px);
    transform: translateY(-50px);
    will-change: transform, filter, opacity;
  }

  .letter.animate {
    animation: blurIn 0.7s ease-out forwards;
  }

  @keyframes blurIn {
    0% {
      filter: blur(10px);
      opacity: 0;
      transform: translateY(-50px);
    }
    50% {
      filter: blur(5px);
      opacity: 0.5;
      transform: translateY(5px);
    }
    100% {
      filter: blur(0px);
      opacity: 1;
      transform: translateY(0);
    }
  }

  .about-text {
    font-size: 25px;
    color: var(--color-white);
    line-height: 1.6;
    text-shadow: 0 0 10px rgba(0,0,0,0.5);
  }

  @media (max-width: 768px) {
    .about-section {
      padding: 80px 15px;
    }
    .about-title {
      font-size: clamp(28px, 7vw, 50px);
    }
    .about-text {
      font-size: clamp(14px, 3vw, 20px);
    }
  }

  @media (max-width: 480px) {
    .about-section {
      padding: 60px 10px;
    }
    .about-title {
      font-size: clamp(24px, 8vw, 40px);
    }
    .about-text {
      font-size: clamp(12px, 4vw, 18px);
    }
  }
</style>
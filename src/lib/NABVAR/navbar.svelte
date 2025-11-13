<!-- Navbar.svelte -->
<script>
  /**
   * @type {{ update: (arg0: (val: any) => boolean) => void; }}
   */
   export let isPlaying;

  let activeLink = 'hogar';

  // IDs corregidos para coincidir con las secciones
  const leftLinks = [
    { id: 'sobre', label: 'Sobre Nosotros' },
    { id: 'videos', label: 'Videos' },
    { id: 'equipo', label: 'Equipo' },
    { id: 'servicios', label: 'Servicios' }
  ];

  const rightLinks = [
    { id: 'eventos', label: 'Eventos' },
    { id: 'photocall', label: 'Photocall' },
    { id: 'contacto', label: 'Contacto' },
  ];

  /**
   * @param {string} id
   * @param {Event} event
   */
  function handleClick(id, event) {
    event.preventDefault();
    activeLink = id;
    smoothScrollTo(id);
  }

  // Función para scroll suave
  function smoothScrollTo(elementId) {
    const element = document.getElementById(elementId);
    if (element) {
      element.scrollIntoView({
        behavior: 'smooth',
        block: 'start',
        inline: 'nearest'
      });
    }
  }

  function togglePlayMusic() {
    isPlaying.update((/** @type {any} */ val) => !val);
  }

  // Función para ir al inicio cuando se hace clic en el logo
  function handleLogoClick() {
    activeLink = 'hogar';
    smoothScrollTo('hogar');
  }
</script>

<nav class="navbar">
  <div class="navbar-wrapper">
    <!-- Links izquierda -->
    <ul class="nav-links nav-left">
      {#each leftLinks as link (link.id)}
        <li>
          <a
            href="#{link.id}"
            class={activeLink === link.id ? 'active' : ''}
            on:click={(e) => handleClick(link.id, e)}
          >
            {link.label}
          </a>
        </li>
      {/each}
    </ul>

    <!-- Logo centrado - Funciona como botón de play/pause -->
    <div class="logo-container">
      <button 
        class="logo-button" 
        on:click={togglePlayMusic}
        class:playing={$isPlaying}
        title={$isPlaying ? 'Pausar música' : 'Reproducir música'}
      >
        <img src="/logo-pequeño.png" alt="ADN Logo" class="logo" />
        
        <!-- Icono de Play (visible cuando está pausado) -->
        <div class="control-icon play-icon" class:visible={!$isPlaying}>
          <svg viewBox="0 0 24 24" fill="currentColor">
            <circle cx="12" cy="12" r="10" fill="none" stroke="currentColor" stroke-width="2"/>
            <polygon points="10 8 10 16 16 12" fill="currentColor"/>
          </svg>
        </div>

        <!-- Icono de Pause (visible cuando está reproduciendo) -->
        <div class="control-icon pause-icon" class:visible={$isPlaying}>
          <svg viewBox="0 0 24 24" fill="currentColor">
            <circle cx="12" cy="12" r="10" fill="none" stroke="currentColor" stroke-width="2"/>
            <rect x="9" y="8" width="2" height="8" fill="currentColor"/>
            <rect x="13" y="8" width="2" height="8" fill="currentColor"/>
          </svg>
        </div>
      </button>
    </div>

    <!-- Links derecha -->
    <ul class="nav-links nav-right">
      {#each rightLinks as link (link.id)}
        <li>
          <a
            href="#{link.id}"
            class={activeLink === link.id ? 'active' : ''}
            on:click={(e) => handleClick(link.id, e)}
          >
            {link.label}
          </a>
        </li>
      {/each}
    </ul>
  </div>
</nav>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Audiowide&family=Rajdhani:wght@400;500;600;700&display=swap');

  :root {
    --color-red: rgb(229, 225, 225);
    --color-red-light: #FF7070;
    --color-pink: #E89A9E;
    --color-brown: #3D2726;
    --color-gray: #808080;
    --color-gray-dark: #4D4D4D;
    --font-family-main: 'Rajdhani', 'Orbitron', sans-serif;
    --font-family-display: 'Audiowide', 'Orbitron', sans-serif;
    --transition-normal: 0.3s ease;
  }

  html, body {
    margin: 0;
    padding: 0;
    width: 100%;
    height: 100%;
    background: #0a0a0a;
    overflow-x: hidden;
  }

  .navbar {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    background: linear-gradient(135deg, rgba(26, 26, 26, 0.98) 0%, rgba(45, 45, 45, 0.98) 100%);
    border-bottom: 2px solid var(--color-red);
    box-shadow: 0 0 30px rgba(255, 51, 51, 0.4), inset 0 0 20px rgba(255, 51, 51, 0.1);
    width: 100%;
    height: 100px;
    z-index: 1000;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .navbar-wrapper {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 20px;
    box-sizing: border-box;
  }

  .nav-links {
    display: flex;
    list-style: none;
    margin: 0;
    padding: 0;
    flex: 1;
  }

  .nav-left {
    justify-content: flex-start;
  }

  .nav-right {
    justify-content: flex-end;
  }

  ul {
    margin: 0;
    padding: 0;
  }

  li {
    position: relative;
  }

  a {
    color: rgb(219, 218, 218);
    text-decoration: none;
    font-size: 20px;
    font-weight: 500;
    padding: 8px 14px;
    border-radius: 4px;
    transition: all var(--transition-normal);
    text-transform: capitalize;
    letter-spacing: 0.5px;
    font-family: var(--font-family-main);
    cursor: pointer;
    display: block;
  }

  a:hover {
    color: #ffffff;
    background-color: rgba(255, 51, 51, 0.15);
    box-shadow: 0 0 15px rgba(255, 51, 51, 0.6),
                inset 0 0 15px rgba(255, 51, 51, 0.2);
    text-shadow: 0 0 15px rgba(255, 51, 51, 0.9),
                 0 0 30px rgba(255, 51, 51, 0.6);
    transform: translateY(-2px);
  }

  a.active {
    color: var(--color-red);
    background: linear-gradient(135deg, rgba(255, 51, 51, 0.25), rgba(255, 51, 51, 0.08));
    border: 1px solid rgba(255, 51, 51, 0.5);
    box-shadow: 0 0 20px rgba(255, 51, 51, 0.8),
                inset 0 0 20px rgba(255, 51, 51, 0.3);
    text-shadow: 0 0 20px rgba(255, 51, 51, 1),
                 0 0 40px rgba(255, 51, 51, 0.7);
    animation: neon-pulse 2s ease-in-out infinite;
  }

  a.active::before {
    content: '';
    position: absolute;
    bottom: -4px;
    left: 0;
    right: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, var(--color-red), transparent);
    box-shadow: 0 0 10px rgba(255, 51, 51, 0.9);
  }

  /* Logo Button */
  .logo-container {
    display: flex;
    align-items: center;
    justify-content: center;
    flex: 0 0 auto;
    margin: 0 40px;
  }

  .logo-button {
    position: relative;
    background: none;
    border: none;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all var(--transition-normal);
    padding: 0;
  }

  .logo {
    height: 70px;
    width: auto;
    object-fit: contain;
    filter: drop-shadow(0 0 15px rgba(255, 51, 51, 0.7))
            drop-shadow(0 0 30px rgba(255, 51, 51, 0.4));
    transition: all var(--transition-normal);
  }

  .logo-button:hover .logo {
    filter: drop-shadow(0 0 20px rgba(255, 51, 51, 0.9))
            drop-shadow(0 0 40px rgba(255, 51, 51, 0.6))
            brightness(1.1)
            drop-shadow(0 0 60px rgba(255, 51, 51, 0.3));
    transform: scale(1.05);
  }

  /* Control Icons (Play/Pause) */
  .control-icon {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0;
    transition: opacity var(--transition-normal);
    pointer-events: none;
  }

  .control-icon.visible {
    opacity: 1;
  }

  .control-icon svg {
    width: 40px;
    height: 40px;
    filter: drop-shadow(0 0 10px rgba(255, 51, 51, 0.9));
    transition: all var(--transition-normal);
  }

  .logo-button:hover .control-icon svg {
    filter: drop-shadow(0 0 15px rgba(255, 51, 51, 1))
            drop-shadow(0 0 25px rgba(255, 51, 51, 0.7));
    transform: scale(1.1);
  }

  /* Animación cuando está reproduciendo */
  .logo-button.playing {
    animation: pulse-button 1.5s ease-in-out infinite;
  }

  .logo-button.playing .pause-icon svg {
    animation: pulse-icon 1.5s ease-in-out infinite;
  }

  @keyframes neon-pulse {
    0%, 100% {
      box-shadow: 0 0 20px rgba(255, 51, 51, 0.8),
                  inset 0 0 20px rgba(255, 51, 51, 0.3);
    }
    50% {
      box-shadow: 0 0 30px rgba(255, 51, 51, 1),
                  inset 0 0 30px rgba(255, 51, 51, 0.5);
    }
  }

  @keyframes pulse-button {
    0%, 100% {
      filter: drop-shadow(0 0 15px rgba(255, 51, 51, 0.7))
              drop-shadow(0 0 30px rgba(255, 51, 51, 0.4));
    }
    50% {
      filter: drop-shadow(0 0 25px rgba(255, 51, 51, 0.9))
              drop-shadow(0 0 50px rgba(255, 51, 51, 0.6));
    }
  }

  @keyframes pulse-icon {
    0%, 100% {
      filter: drop-shadow(0 0 10px rgba(255, 51, 51, 0.9));
    }
    50% {
      filter: drop-shadow(0 0 20px rgba(255, 51, 51, 1))
              drop-shadow(0 0 35px rgba(255, 51, 51, 0.8));
    }
  }

  @media (max-width: 768px) {
    .navbar {
      height: 80px;
    }
    
    a {
      font-size: 16px;
      padding: 6px 10px;
    }

    .logo-container {
      margin: 0 20px;
    }

    .logo {
      height: 50px;
    }

    .control-icon svg {
      width: 30px;
      height: 30px;
    }
  }

  @media (max-width: 480px) {
    .navbar {
      height: 70px;
    }

    a {
      font-size: 12px;
      padding: 4px 6px;
    }

    .logo-container {
      margin: 0 10px;
    }

    .logo {
      height: 40px;
    }

    .control-icon svg {
      width: 20px;
      height: 20px;
    }
  }
</style>
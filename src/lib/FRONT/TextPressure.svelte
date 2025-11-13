<script>
  import { onMount } from 'svelte';

  export let text = 'BAMBOLEO';
  export let className = ''; // nueva propiedad para pasar clases adicionales
  
  let containerEl;
  let chars = [];

  onMount(() => {
    chars = text.split('');

    const container = containerEl;
    let mouseX = 0;
    let mouseY = 0;

    const handleMouseMove = (e) => {
      mouseX = e.clientX;
      mouseY = e.clientY;

      chars.forEach((_, index) => {
        const charEl = container?.children[index];
        if (!charEl) return;

        const rect = charEl.getBoundingClientRect();
        const charX = rect.left + rect.width / 2;
        const charY = rect.top + rect.height / 2;

        const distance = Math.sqrt(
          Math.pow(mouseX - charX, 2) + Math.pow(mouseY - charY, 2)
        );

        const maxDistance = 200;
        const pressure = Math.max(0, 1 - distance / maxDistance);
        const scale = 1 + pressure * 0.3;
        const weight = 400 + pressure * 500;

        charEl.style.transform = `scale(${scale})`;
        charEl.style.fontWeight = weight;
      });
    };

    document.addEventListener('mousemove', handleMouseMove);

    return () => {
      document.removeEventListener('mousemove', handleMouseMove);
    };
  });
</script>

<h1 class="main-title {className}" bind:this={containerEl}>
  {#each chars as char, i (i)}
    <span class="char">{char}</span>
  {/each}
</h1>

<style>
  .main-title {
    font-family: 'Audiowide', 'Orbitron', sans-serif;
    font-size: clamp(48px, 12vw, 120px);
    font-weight: 700;
    color: #FFFFFF;
    margin: 0;
    padding: 0;
    text-shadow: 0 0 30px rgba(255, 51, 51, 0.8),
                 0 0 60px rgba(255, 51, 51, 0.5),
                 0 0 90px rgba(255, 51, 51, 0.3);
    letter-spacing: 3px;
    font-style: italic;
    display: flex;
    justify-content: center;
    gap: 0.1em;
  }

  .char {
    display: inline-block;
    transition: all 0.1s ease-out;
  }

  /* Estilos opcionales para subtitle */
  .subtitle {
    font-size: clamp(32px, 8vw, 80px);
    color: #FF3333;
    text-shadow: 0 0 20px rgba(255, 51, 51, 0.9),
                 0 0 40px rgba(255, 51, 51, 0.6);
    letter-spacing: 2px;
    font-style: italic;
  }
</style>

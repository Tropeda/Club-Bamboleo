<script>

  const hosts = [
    {
      name: "DJs EL GRECO",
      role: "Dj Oficiale",
      image: "/dj.avif", 
    },
    {
      name: "PAULA RUEDA",
      role: "Gerente de Fiesta",
      image: "/gerente.avif", 
    },
    {
      name: "ARRIQUITAUN",
      role: "Animadora Residente",
      image: "/animador.jpg", 
    },
    {
      name: "EL ENCONAO",
      role: "Artista Invitado",
      image: "/artista.jpg", 
    },
  ];
</script>

<section class="hosts-section">
  <h3>Conoce a los Nuestros</h3>
  <h2>NUESTROS ANFITRIONES DE LA FIESTA</h2>

  <div class="hosts-grid">
    {#each hosts as host}
      <div class="host-card">
        <img src={host.image} alt={host.name} />
        <h4>{host.name}</h4>
        <p>{host.role}</p>
      </div>
    {/each}
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

  .hosts-section {
    text-align: center;
    padding: 4rem 1rem;
    background-color: #000000;
    color: white;
  }

  .hosts-section h3 {
    color: var(--color-red);
    font-family: 'Audiowide', sans-serif;
    font-size: 1.5rem;
    margin-bottom: 0.5rem;
  }

  .hosts-section h2 {
    font-size: 2.5rem;
    margin-bottom: 5rem;
    font-family: 'Orbitron', sans-serif;
  }

  .hosts-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 2rem;
    justify-items: center;
  }

  .host-card {
    background-color: var(--color-red);
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 4px 15px rgba(0,0,0,0.5);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    width: 100%;
    max-width: 250px;
    text-align: center;
  }

  .host-card img {
    width: 100%;
    height: 250px;
    object-fit: cover;
  }

  .host-card h4 {
    margin: 1rem 0 0.5rem 0;
    font-family: 'Orbitron', sans-serif;
    font-size: 1.25rem;
  }

  .host-card p {
    margin-bottom: 1rem;
    color:white;
    font-family: 'Audiowide', sans-serif;
  }

  .host-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 8px 20px rgba(0,0,0,0.7);
  }

  /* Responsivo */
  @media (max-width: 768px) {
    .hosts-section h2 {
      font-size: 2rem;
    }
  }

  @media (max-width: 480px) {
    .hosts-section h2 {
      font-size: 1.5rem;
    }
  }
</style>

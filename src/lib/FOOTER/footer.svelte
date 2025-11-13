<script>
  const year = new Date().getFullYear();
</script>

<footer class="footer">
  <div class="footer-overlay"></div>

  <div class="footer-content">
    <!-- LOGO + DESCRIPCIÓN -->
    <div class="footer-section about">
      <h2 class="footer-logo">BAMBOLEO <span>CLUB</span></h2>
      <p class="footer-description">
        Vive la noche como nunca antes.  
        Ritmo, luces y energía en cada latido.  
        Bienvenido a la experiencia <strong>Bamboleo</strong>.
      </p>
    </div>

    <!-- ENLACES RÁPIDOS -->
    <div class="footer-section links">
      <h3>Explora</h3>
      <ul>
        <li><a href="#eventos">Eventos</a></li>
        <li><a href="#galeria">Galería</a></li>
        <li><a href="#contacto">Contacto</a></li>
      </ul>
    </div>

    <!-- REDES SOCIALES -->
    <div class="footer-section social">
      <h3>Síguenos</h3>
      <div class="social-links">
        <a href="#" aria-label="Instagram"><i class="fab fa-instagram"></i></a>
        <a href="#" aria-label="TikTok"><i class="fab fa-tiktok"></i></a>
      </div>
    </div>
  </div>

  <div class="footer-bottom">
    <p>© {year} Bamboleo Club. Todos los derechos reservados.</p>
  </div>
</footer>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Audiowide&family=Orbitron:wght@400;700&display=swap');
  @import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css');

  .footer {
    position: relative;
    background: radial-gradient(circle at top, #1a1a1a 0%, #000 100%);
    color: #fff;
    padding: 80px 40px 40px;
    overflow: hidden;
    font-family: 'Orbitron', 'Audiowide', sans-serif;
    z-index: 10;
  }

  .footer-overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: black;
    z-index: 1;
  }

  .footer-content {
    position: relative;
    z-index: 2;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    gap: 40px;
    max-width: 1200px;
    margin: 0 auto;
  }

  .footer-section {
    flex: 1 1 300px;
  }

  .footer-logo {
    font-size: 2.2rem;
    color: #ff3b3b;
    letter-spacing: 2px;
    margin-bottom: 15px;
    text-shadow: 0 0 15px rgba(255, 0, 0, 0.6);
  }

  .footer-logo span {
    color: #fff;
  }

  .footer-description {
    font-size: 0.95rem;
    line-height: 1.6;
    color: #ccc;
    max-width: 350px;
  }

  .footer-section h3 {
    font-size: 1.2rem;
    color: #ff3b3b;
    margin-bottom: 15px;
    text-transform: uppercase;
    margin-top: 40px;
    margin-left: 60px;
  }

  .footer-section ul {
    list-style: none;
    padding: 0;
    margin: 0;
    margin-left: 60px;
  }

  .footer-section ul li {
    margin: 10px 0;
  }

  .footer-section ul li a {
    color: #ccc;
    text-decoration: none;
    transition: color 0.3s ease;
  }

  .footer-section ul li a:hover {
    color: #ff3b3b;
  }

  .social-links {
    display: flex;
    gap: 20px;
    margin-top: 10px;
     margin-left: 60px;
  }

  .social-links a {
    color: #fff;
    font-size: 1.4rem;
    transition: transform 0.3s ease, color 0.3s ease;
  }

  .social-links a:hover {
    color: #ff3b3b;
    transform: scale(1.2);
  }

  .footer-bottom {
    position: relative;
    z-index: 2;
    text-align: center;
    margin-top: 60px;
    border-top: 1px solid rgba(255, 255, 255, 0.1);
    padding-top: 20px;
    font-size: 0.9rem;
    color: #aaa;
  }

  @media (max-width: 768px) {
    .footer-content {
      flex-direction: column;
      align-items: center;
      text-align: center;
    }

    .footer-description {
      max-width: 100%;
    }
  }
</style>

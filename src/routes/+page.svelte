<script lang="ts">
    import { writable } from 'svelte/store';
    import Navbar from "$lib/NABVAR/navbar.svelte";
    import Front from "$lib/FRONT/front.svelte";
    import About from "$lib/ABOUT/about.svelte";
    import Videos from '$lib/VIDEOS/videos.svelte';
    import Staff from '$lib/STAFF/staff.svelte';
    import Servicios from '$lib/SERVICIOS/servicios.svelte';
    import Eventos from '$lib/EVENTOS/eventos.svelte';
    import Fotos from '$lib/FOTOS/fotos.svelte';
    import Contacto from '$lib/CONTACTO/contacto.svelte';
    import Footer from '$lib/FOOTER/footer.svelte';

    const isPlaying = writable(false);
</script>

<Navbar {isPlaying} />

<!-- Sección inicial / Hero -->
<section id="hogar">
    <Front {isPlaying} />
</section>

<!-- Sobre Nosotros -->
<section id="sobre">
    <About />
</section>

<!-- Videos -->
<section id="videos">
    <Videos />
</section>

<!-- Equipo / Staff -->
<section id="equipo">
    <Staff />
</section>

<!-- Servicios -->
<section id="servicios">
    <Servicios />
</section>

<!-- Eventos -->
<section id="eventos">
    <Eventos />
</section>

<!-- Photocall / Fotos -->
<section id="photocall">
    <Fotos />
</section>

<!-- Contacto -->
<section id="contacto">
    <Contacto />
</section>

<Footer />

<style>
    /* Scroll suave en toda la página */
    :global(html) {
        scroll-behavior: smooth;
    }

    /* Asegura que las secciones no queden ocultas bajo la navbar */
    section[id] {
        scroll-margin-top: 100px; /* Ajustado a la altura de tu navbar */
    }

    /* Resetea estilos de sección para que no interfieran */
    section {
        display: block;
        width: 100%;
    }

    /* Ajuste para móviles */
    @media (max-width: 768px) {
        section[id] {
            scroll-margin-top: 80px;
        }
    }

    @media (max-width: 480px) {
        section[id] {
            scroll-margin-top: 70px;
        }
    }
</style>
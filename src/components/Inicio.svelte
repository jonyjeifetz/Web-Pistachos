<script>
  import { onMount } from "svelte";

  let recetasContainer;
  let scrollInterval;

  onMount(() => {
    // Lógica para que el scroll se pase solo
    const startAutoScroll = () => {
      scrollInterval = setInterval(() => {
        if (recetasContainer) {
          recetasContainer.scrollLeft += 1; 
          // Si llega a la mitad (final de la primera tanda), vuelve al inicio
          if (recetasContainer.scrollLeft >= recetasContainer.scrollWidth / 2) {
            recetasContainer.scrollLeft = 0;
          }
        }
      }, 30); // Velocidad del movimiento
    };

    // Lógica para que en móviles la receta del centro active el nombre y botón
    const handleMobileScroll = () => {
      const items = document.querySelectorAll('.receta');
      const centerX = window.innerWidth / 2;

      items.forEach(item => {
        const rect = item.getBoundingClientRect();
        // Si el centro de la receta está en el centro de la pantalla
        if (rect.left < centerX && rect.right > centerX) {
          item.classList.add('active-center');
        } else {
          item.classList.remove('active-center');
        }
      });
    };

    startAutoScroll();
    recetasContainer.addEventListener('scroll', handleMobileScroll);

    // Pausas al interactuar
    const stopScroll = () => clearInterval(scrollInterval);
    const resumeScroll = () => startAutoScroll();

    recetasContainer.addEventListener('mouseenter', stopScroll);
    recetasContainer.addEventListener('mouseleave', resumeScroll);
    recetasContainer.addEventListener('touchstart', stopScroll);
    recetasContainer.addEventListener('touchend', resumeScroll);

    return () => clearInterval(scrollInterval);
  });
</script>

<h1>De La Rioja al mundo: nuestro alcance</h1>
<div id="flourish-container">
  <div class="flourish-embed flourish-map" data-src="visualisation/20858873"></div>
</div>

<h1>De La Rioja a Tu Mesa: Recetas Creativas con Pistacho</h1>
<div class="recetas-container" bind:this={recetasContainer}>
  <div class="recetas">
    {#each [1, 2] as loop}
      <div class="receta">
        <img src="./images/Brownie de Pistacho.jpeg" alt="Brownie de Pistacho" />
        <div class="hover-text">Brownie de Pistacho</div>
        <a href="./Recetas/Receta Brownie de Pistacho.pdf" target="_blank" class="btn-ver-receta">Ver receta</a>
      </div>
      <div class="receta">
        <img src="./images/Baklava.jpeg" alt="Baklava" />
        <div class="hover-text">Baklava de Pistacho</div>
        <a href="./Recetas/Receta Baklava de Pistacho.pdf" target="_blank" class="btn-ver-receta">Ver receta</a>
      </div>
      <div class="receta">
        <img src="./images/Queso.jpeg" alt="Queso" />
        <div class="hover-text">Queso con Pistacho</div>
        <a href="./Recetas/Receta Queso de Pistacho.pdf" target="_blank" class="btn-ver-receta">Ver receta</a>
      </div>
      <div class="receta">
        <img src="./images/Crema de Pistacho.jpeg" alt="Crema de Pistacho" />
        <div class="hover-text">Crema de Pistacho</div>
        <a href="./Recetas/Receta Crema Pistacho.pdf" target="_blank" class="btn-ver-receta" >Ver receta</a>
      </div>
      <div class="receta">
        <img src="./images/Trufas.jpeg" alt="Trufas de Pistacho" />
        <div class="hover-text">Trufas de Pistacho, Palta y Chocolate</div>
        <a href="./Recetas/Receta Trufas de Pistacho, Palta y Chocolate.pdf" target="_blank" class="btn-ver-receta">Ver receta</a>
      </div>
    {/each}
  </div>
</div>

<style>
    h1 {
        font-family: montserrat;
        color: #FFFFFF;
        text-align: center;
        margin-top: 40px;
    }

    /* Recetas */
  .recetas-container {
      display: flex;
      justify-content: flex-start;
      width: 100%;
      padding: 40px 0;
      margin-bottom: 20px;
      overflow-x: auto;
      scrollbar-width: none;
  }

  .recetas-container::-webkit-scrollbar {
      display: none;
  }

  .recetas {
      display: flex;
      gap: 20px;
      width: max-content;
      flex-wrap: nowrap;
      padding: 0 20px;
  }

  .receta {
      position: relative;
      width: 300px;
      height: 400px;
      text-align: center;
      flex-shrink: 0;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      transition: transform 0.4s ease;
      overflow: hidden;
      border-radius: 10px;
  }

  .receta img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: all 0.4s ease;
  }

  /* Efecto hover para PC */
  @media (min-width: 769px) {
    .receta:hover img {
        transform: scale(1.1);
        filter: brightness(0.6);
    }
    .receta:hover .hover-text,
    .receta:hover .btn-ver-receta {
        opacity: 1;
    }
  }

  /* Hover-text */
  .hover-text {
      position: absolute;
      top: 40%;
      color: white;
      font-size: 24px;
      font-weight: bold;
      padding: 10px;
      opacity: 0;
      transition: opacity 0.4s ease;
      z-index: 2;
      text-shadow: 2px 2px 4px rgba(0,0,0,0.8);
  }

  /* Botón */
  .btn-ver-receta {
      position: absolute;
      bottom: 20%;
      background-color: black;
      color: white;
      padding: 10px 20px;
      border-radius: 20px;
      text-decoration: none;
      font-weight: bold;
      opacity: 0;
      transition: all 0.4s ease;
      z-index: 2;
  }

  /* Efecto para Móviles (Activo al estar en el centro) */
  :global(.receta.active-center img) {
      transform: scale(1.1);
      filter: brightness(0.6);
  }
  :global(.receta.active-center .hover-text),
  :global(.receta.active-center .btn-ver-receta) {
      opacity: 1;
  }

  /* Ajustes Responsive */
  @media (max-width: 768px) {
      .receta {
          width: 250px;
          height: 350px;
      }
      .hover-text {
          font-size: 18px;
      }
  }

  .flourish-embed {
    width: 100%;
    max-width: 100%;
    overflow-x: hidden;
  }

  * {
    box-sizing: border-box;
  }
</style>
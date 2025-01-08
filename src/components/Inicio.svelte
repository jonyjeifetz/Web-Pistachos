<!-- Mapa -->
<h1>De La Rioja al mundo: nuestro alcance</h1>
<div class="flourish-embed flourish-map" data-src="visualisation/20858873"><script src="https://public.flourish.studio/resources/embed.js"></script><noscript><img src="https://public.flourish.studio/visualisation/20858873/thumbnail" width="100%" alt="map visualization" /></noscript></div>
<br>

<!-- Recetas -->
<h1>De La Rioja a Tu Mesa: Recetas Creativas con Pistacho</h1>
<div class="recetas-container">
  <div class="recetas">
    <!-- Receta 1 -->
    <div class="receta">
      <img src="./images/Brownie de Pistacho.jpeg" alt="Brownie de Pistacho" />
      <div class="hover-text">Brownie de Pistacho</div>
      <a href="./Recetas/Receta Brownie de Pistacho.pdf" target="_blank" class="btn-ver-receta">Ver receta</a>
    </div>
    <!-- Receta 2 -->
    <div class="receta">
      <img src="./images/Baklava.jpeg" alt="Baklava" />
      <div class="hover-text">Baklava de Pistacho</div>
      <a href="./Recetas/Receta Baklava de Pistacho.pdf" target="_blank" class="btn-ver-receta">Ver receta</a>
    </div>
    <!-- Receta 3 -->
    <div class="receta">
      <img src="./images/Queso.jpeg" alt="Queso" />
      <div class="hover-text">Queso con Pistacho</div>
      <a href="./Recetas/Receta Queso de Pistacho.pdf" target="_blank" class="btn-ver-receta">Ver receta</a>
    </div>
    <!-- Receta 4 -->
    <div class="receta">
      <img src="./images/Crema de Pistacho.jpeg" alt="Crema de Pistacho" />
      <div class="hover-text">Crema de Pistacho</div>
      <a href="./Recetas/Receta Crema Pistacho.pdf" target="_blank" class="btn-ver-receta" >Ver receta</a>
    </div>
    <!-- Receta 5 -->
    <div class="receta">
      <img src="./images/Trufas.jpeg" alt="Trufas de Pistacho" />
      <div class="hover-text">Trufas de Pistacho, Palta y Chocolate</div>
      <a href="./Recetas/Receta Trufas de Pistacho, Palta y Chocolate.pdf" target="_blank" class="btn-ver-receta">Ver receta</a>
    </div> 
  </div>
</div>

<style>

    h1, h3 {
        font-family: montserrat;
        color: #FFFFFF;
        text-align: center;
    }

    /* Recetas */
  .recetas-container {
      display: flex;
      justify-content: flex-start;
      width: 100%;
      padding: 20px;
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
  }

  .receta {
      position: relative;
      width: 300px;  /* Tamaño base para pantallas grandes */
      height: 400px;
      text-align: center;
      flex-shrink: 0;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      transition: transform 0.3s ease;
  }

  /* Ajuste de tamaño de imagen */
  .receta img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.3s ease;
      border-radius: 10px;
  }

  /* Efecto hover para dispositivos con mouse */
  .receta:hover img {
      transform: scale(1.1);  /* Agranda la imagen cuando se hace hover */
  }

  /* Hover-text */
  .hover-text {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background-color: black;
      color: white;
      font-size: 24px;
      font-weight: bold;
      padding: 10px;
      border-radius: 10px;
      opacity: 0;
      transition: opacity 0.3s ease;
  }

  .receta:hover .hover-text {
      opacity: 1;  /* Muestra el texto cuando la receta tiene hover */
  }

  /* Botón */
  .btn-ver-receta {
      background-color: black;
      color: white;
      padding: 10px 20px;
      border-radius: 20px;
      text-decoration: none;
      font-weight: bold;
      opacity: 0;
      transition: opacity 0.3s ease, transform 0.3s ease;
      margin: 0 auto;
      width: fit-content;
      position: relative;
      z-index: 1;
  }

  .receta:hover .btn-ver-receta {
      opacity: 1;
      transform: translateY(-10px) scale(1.1);  /* Efecto en el botón */
  }

  /* Ajustes para dispositivos pequeños */
  @media (max-width: 768px) {
      .receta {
          width: 250px;  /* Reduce el tamaño de cada receta en pantallas pequeñas */
          height: 350px;
      }

      .receta img {
          width: 100%;
          height: auto;  /* Ajuste para que las imágenes se mantengan proporcionadas */
      }
  }

  /* Ajustes para dispositivos aún más pequeños */
  @media (max-width: 480px) {
      .receta {
          width: 200px;  /* Ajuste para pantallas aún más pequeñas */
          height: 300px;
      }

      .receta img {
          width: 100%;
          height: auto;
      }

      .hover-text {
          font-size: 18px;  /* Ajusta el tamaño de la fuente para pantallas pequeñas */
          padding: 5px;
      }

      .btn-ver-receta {
          font-size: 14px;  /* Reduce el tamaño del texto en el botón */
          padding: 8px 16px;  /* Ajusta el tamaño del botón */
      }
  }

  /* Efecto hover automático para imágenes en dispositivos táctiles con 70% de visibilidad */
  .receta img {
      transition: transform 0.3s ease;
  }

  /* Hover automático para dispositivos táctiles, cuando la imagen es visible al 70% */
  .receta.hover img {
      transform: scale(1.1); /* Agranda la imagen cuando está al 70% visible */
  }

  /* Efecto hover en dispositivos con mouse */
  .receta.mouse-hover:hover img {
      transform: scale(1.1); /* Efecto hover manual */
  }

  .receta.show-hover img {
    transform: scale(1.1);  /* Agranda la imagen cuando se activa el hover */
}

/* Borrado de marca de agua flourish */
.flourish-embed {
    width: 100%;
    max-width: 100%; /* Impide que el mapa se salga de la pantalla */
    overflow-x: hidden; /* Evita el desplazamiento horizontal del mapa */
  }

  * {
    box-sizing: border-box; /* Asegura que los márgenes y rellenos no causen desbordes */
  }
</style>
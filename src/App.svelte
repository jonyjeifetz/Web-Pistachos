<!-- Codigo J-S -->

<script>
  window.onload = function() {
    // Número de WhatsApp al que quieres que se envíen los mensajes
    var phoneNumber = "+5491127161950"; // Cambia este número por el que prefieras 

    // El mensaje preescrito de WhatsApp, Gmail e Instagram
    var prewrittenMessage = "¡Hola! Estoy interesado en saber más sobre los pistachos de La Rioja.";
    var encodedMessage = encodeURIComponent(prewrittenMessage);

    // Dirección de correo para Gmail
    var emailAddress = "info@pistachosriojanos.com"; // Cambia esto por la dirección de correo a la que deseas enviar el mensaje

    // Enlaces de los iconos
    var instagramLink = document.getElementById("instagram-link");
    var whatsappLink = document.getElementById("whatsapp-link");
    var gmailLink = document.getElementById("gmail-link");

    // Detecta el dispositivo
    var isMobile = /iPhone|iPad|iPod|Android/i.test(navigator.userAgent);

    // WhatsApp
    if (isMobile && isMobile != "iPad") {
      // Si es móvil, abre la app de WhatsApp
      whatsappLink.href = "https://wa.me/" + phoneNumber + "?text=" + encodedMessage;
    } else {
      // Si es computadora, abre WhatsApp Web
      whatsappLink.href = "https://web.whatsapp.com/send?phone=" + phoneNumber + "&text=" + encodedMessage;
    }

    // Instagram
    if (isMobile && isMobile != "iPad") {
      // Si es móvil, abre la app de Instagram
      instagramLink.href = "instagram://user?username=pistachosriojanos";  // Cambia 'tu_usuario' por tu nombre de usuario en Instagram
    } else {
      // Si es computadora, abre Instagram Web
      instagramLink.href = "https://www.instagram.com/pistachosriojanos";  // Cambia 'tu_usuario' por tu nombre de usuario en Instagram
    }

    // Gmail
    if (isMobile) {
      // Si es móvil, abre la app de Gmail
      gmailLink.href = "mailto:" + emailAddress + "?subject=Mas Informacion&body=" + encodedMessage; // En el "?subject=......&body="" puedes cambiar el asunto del correo
    } else {
      // Si es computadora, abre Gmail Web
      gmailLink.href = "https://mail.google.com/mail/?view=cm&fs=1&to=" + emailAddress + "&su=Mas%20Informacion&body=" + encodedMessage; // En el "&su=......&body=" puedes cambiar el asunto del correo
    }
  };
</script>



<!-- Codigo HTML -->

<body>
  <main>
    <!-- Header -->
    <div class="header">
      <img
        src="./images/Logo-Pistachos.png"
        alt="Logo-Pistachos-Riojanos"
      />
    </div> 
    <!-- Cuerpo -->
    <div class="cuerpo">
      <h1>De La Rioja al mundo: nuestro alcance</h1>
      <div class="flourish-embed flourish-map" data-src="visualisation/20858873"><script src="https://public.flourish.studio/resources/embed.js"></script><noscript><img src="https://public.flourish.studio/visualisation/20858873/thumbnail" width="100%" alt="map visualization" /></noscript></div>
      <p>En esta página encontrarás información sobre los pistachos de La Rioja, su cultivo, propiedades y recetas.</p>
      <p>¡Esperamos que te guste!</p>
      <!-- Enters para que el Footer quede al final de la Pantalla. Es provisorio hasta que tenga toda la info -->
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <br>
      <!-- Aca terminan los enters Provisorios -->
    </div>
    <!-- Footer -->
    <div class="footer">
      <!-- Titulo del Footer -->
       <h4 style="font-family: montserrat; text-allign: center; margin-top: -0.4%;">¿Preguntas? ¡Estamos a un clic de distancia!</h4>
      <!-- Instagram -->
      <a id="instagram-link" href="#" target="_blank">
        <img
          src="./images/Instagram.png"
          alt="Instagram"
        />
      </a>
      <!-- WhatsApp -->
      <a id="whatsapp-link" href="#" target="_blank">
        <img
          src="./images/What's App.png"
          alt="What's App"
        />
      </a>
      <!-- Gmail -->
      <a id="gmail-link" href="#" target="_blank">
        <img
          src="./images/Gmail.png"
          alt="Gmail"
        />
      </a>
    </div> 
  </main>
</body>



<!-- Codigo CSS -->

<style>
 body{
  background-color:#80A54D; /* Color Pistacho */
  font-family: Arial, sans-serif; /* Fuente básica */
  margin: 0; /* Elimina el margen por defecto del body */
  padding: 0; /* Elimina el relleno por defecto del body */
  overflow-x: hidden; /* Evita el scroll horizontal */
  width: 100%; /* Ajusta el ancho al 100% */
 }

 .cuerpo{
  margin: 8px; /* Margen predeterminado */
  padding: 0;  /* Relleno desactivado para evitar inconsistencias */
  text-align: center; /* Centra el contenido */
  flex: 1; /* Ocupa el espacio restante entre el header y el footer */
 }

 .cuerpo h1 {
    font-family: montserrat;
    color: #FFFFFF;
  }

  .cuerpo p {
    font-family: roboto;
    color: #FFFFFF;
    padding: 1rem 0;
  }

 .header{
  background-color: #FFFFFF; /* Color de fondo */
  text-align: center; /* Centra el contenido */
 }

 .header img {
  max-width: 100%; /* Hace que la imagen no se salga del contenedor */
  height: auto; /* Mantiene la relación de aspecto */
 }

 .footer{
  background-color: #FFFFFF; /* Color de fondo */
  text-align: center; /* Centra el contenido */
  padding: 0.3rem 0; /* Espacio interno arriba y abajo */
  width: 100%; /* Ajusta el ancho al 100% */
  /*margin-top: 2rem; /* Espacio exterior superior */
 }

 .footer img {
  max-width: 100%; /* Hace que las imágenes no se salgan del contenedor */
  height: auto; /* Mantiene la relación de aspecto */
  margin: 0 2.5rem; /* Añade margen horizontal entre las imágenes */
 }

 .flourish-embed {
  width: 100%;
  max-width: 100%; /* Impide que el mapa se salga de la pantalla */
  overflow-x: hidden; /* Evita el desplazamiento horizontal del mapa */
}

* {
  box-sizing: border-box; /* Asegura que los márgenes y rellenos no causen desbordes */
}

</style>

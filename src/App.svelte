<script>
  import { onMount } from "svelte";
  import { Router, Route, Link } from 'svelte-routing';
  import Inicio from './components/Inicio.svelte';
  import AcercaDeNosotros from './components/AcercaDeNosotros.svelte';
  import AcercaDelPistacho from './components/AcercaDelPistacho.svelte';
  import UltimasNoticiasDelPistacho from './components/UltimasNoticiasDelPistacho.svelte';
  import ResposabilidadSocialEmpresarial from './components/ResposabilidadSocialEmpresarial.svelte';
  import NuestraGente from './components/NuestraGente.svelte';

  onMount(() => {
    if (window.location.pathname !== "/") {
      window.location.href = "/";
    }
    
    // Establecer enlaces de WhatsApp, Instagram y Gmail según el dispositivo
    const phoneNumber = "+5491127161950"; 
    const prewrittenMessage = "¡Hola! Estoy interesado en saber más sobre los pistachos de La Rioja.";
    const encodedMessage = encodeURIComponent(prewrittenMessage);
    const emailAddress = "info@pistachosriojanos.com"; 
    
    const isMobile = /iPhone|iPad|iPod|Android/i.test(navigator.userAgent);
    
    document.getElementById("whatsapp-link").href = isMobile ? 
      `https://wa.me/${phoneNumber}?text=${encodedMessage}` : 
      `https://web.whatsapp.com/send?phone=${phoneNumber}&text=${encodedMessage}`;

    document.getElementById("instagram-link").href = isMobile ? 
      "instagram://user?username=pistachosriojanos" : 
      "https://www.instagram.com/pistachosriojanos";

    document.getElementById("gmail-link").href = isMobile ? 
      `mailto:${emailAddress}?subject=Mas Informacion&body=${encodedMessage}` : 
      `https://mail.google.com/mail/?view=cm&fs=1&to=${emailAddress}&su=Mas%20Informacion&body=${encodedMessage}`;
  });

  function toggleMenu() {
    const menu = document.querySelector('.menu');
    menu.classList.toggle('active');
  }

  onMount(() => {
    const menuLinks = document.querySelectorAll('.menu ul li a');
    menuLinks.forEach(link => {
      link.addEventListener('click', () => {
        document.querySelector('.menu').classList.remove('active');
      });
    });
  });
</script>

<body>
  <main>
    <div class="header"> 
      <img src="./images/Logo-Pistachos.png" alt="Logo-Pistachos-Riojanos" />
    </div>  

    <Router>
      <!-- Botón para menú desplegable en móviles -->
      <button class="menu-button" on:click={toggleMenu}>☰ Menú</button>

      <!-- Menú desplegable -->
      <nav class="menu">
        <button class="close-btn" on:click={toggleMenu}>X</button>
        <ul>
          <li><a href="#">Inicio</a></li>
          <li><a href="#">Acerca de Nosotros</a></li>
          <li><a href="#">Acerca del Pistacho</a></li>
          <li><a href="#">Últimas Noticias del Pistacho</a></li>
          <li><a href="#">Responsabilidad Social Empresarial</a></li>
          <li><a href="#">Nuestra Gente</a></li>
        </ul>
      </nav>

      <!-- Menú horizontal para pantallas grandes -->
      <nav class="menu-horizontal">
        <ul>
          <li><Link to="/">Inicio</Link></li>
          <li><Link to="/acerca-de-nosotros">Acerca de Nosotros</Link></li>
          <li><Link to="/acerca-del-pistacho">Acerca del Pistacho</Link></li>
          <li><Link to="/ultimas-noticias-del-pistacho">Últimas Noticias del Pistacho</Link></li>
          <li><Link to="/responsabilidad-social-empresarial">Responsabilidad Social Empresarial</Link></li>
          <li><Link to="/nuestra-gente">Nuestra Gente</Link></li>
        </ul>
      </nav>

      <!-- Rutas -->
      <Route path="/" component={Inicio} />
      <Route path="/acerca-de-nosotros" component={AcercaDeNosotros} />
      <Route path="/acerca-del-pistacho" component={AcercaDelPistacho} />
      <Route path="/ultimas-noticias-del-pistacho" component={UltimasNoticiasDelPistacho} />
      <Route path="/responsabilidad-social-empresarial" component={ResposabilidadSocialEmpresarial} />
      <Route path="/nuestra-gente" component={NuestraGente} />
    </Router>

    <!-- Footer -->
    <div class="footer">
      <h4>¿Preguntas? ¡Estamos a un clic de distancia!</h4>
      <div class="social-icons">
        <a id="instagram-link" href="#" target="_blank"><img src="./images/Instagram.png" alt="Instagram" /></a>
        <a id="whatsapp-link" href="#" target="_blank"><img src="./images/What's App.png" alt="Whats App" /></a>
        <a id="gmail-link" href="#" target="_blank"><img src="./images/Gmail.png" alt="Gmail" /></a>
      </div>
      <div class="footer-copy">
        <p>© 2024 por Jonathan Jeifetz</p>
      </div>
    </div>
  </main>
</body>

<style>
/* Estilos generales */
body {
  background-color: #80A54D;
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  overflow-x: hidden;
  width: 100%;
}

.header {
  background-color: #FFFFFF;
  padding: 20px 0;
  text-align: center;
}

.header img {
  max-width: 100%;
  height: auto;
  display: block;
  margin: 0 auto;
}

.footer {
  background-color: #FFFFFF;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px 0;
}

.footer h4 {
  font-family: montserrat;
  margin-top: 0;
  margin-bottom: 20px;
}

.footer .social-icons {
  display: flex;
  justify-content: center;
  gap: 50px; /* Espacio entre iconos */
  flex-wrap: wrap;
  padding: 1rem;
}

.footer img {
  max-width: 50px;
  height: auto;
}

.footer-copy {
  margin-top: 20px;
  font-size: 14px;
  color: #666;
  text-align: center;
}

/* Estilos para el menú */
nav {
  background-color: rgb(0, 0, 0);
  padding: 10px;
}

nav ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
  display: flex;
  justify-content: center;
}

nav li {
  margin-right: 20px;
}

nav ul li a {
  color: white;
  text-decoration: none;
  font-size: 19px;
}

nav ul li a:hover {
  text-decoration: underline;
}

/* Menú en dispositivos móviles */
@media (max-width: 600px) {
  .menu {
    display: none;
    position: absolute;
    top: 50px;
    left: 0;
    width: 100%;
    background-color: #333;
    text-align: center;
    padding-top: 20px;
    z-index: 1000;
  }

  .menu.active {
    display: block;
  }

  .menu ul {
    display: block;
    padding: 0;
  }

  .menu ul li {
    margin: 20px 0;
  }

  .menu ul li a {
    color: white;
    font-size: 20px;
    text-decoration: none;
  }

  .menu ul li a:hover {
    color: #FFD700;
    text-decoration: underline;
  }

  .menu-button {
    display: block;
    background-color: transparent;
    border: none;
    font-size: 30px;
    color: white;
    cursor: pointer;
  }

  .close-btn {
    display: block;
    background-color: transparent;
    border: none;
    font-size: 30px;
    color: white;
    cursor: pointer;
  }

  .menu-horizontal {
    display: none;  /* No mostrar el menú horizontal en pantallas pequeñas */
  }
}

@media (min-width: 601px) {
  .menu-horizontal {
    display: flex;
    justify-content: space-around;
  }

  .menu-button {
    display: none;
  }

  .menu {
    display: none;  /* No mostrar el menú desplegable en pantallas grandes */
  }
}
</style>

<script lang="ts">
  import { onMount } from 'svelte';

  let menu:number = 0;
  const videoId = "GNkO2hzXluU"


  let characters = ['uranium', '☢️', '🧪'];

  let confetti = new Array(100).fill(0, 0, 100)
  .map((_, i) => {
    return {
      character: characters[i % characters.length],
      x: Math.random() * 100,
      y: -20 - Math.random() * 100,
      r: 0.1 + Math.random() * 1
    };
  })
  .sort((a, b) => a.r - b.r);

  onMount(() => {
    let frame: number;

    function loop() {
      frame = requestAnimationFrame(loop);

      confetti = confetti.map(emoji => {
        emoji.y += 0.7 * emoji.r;
        if (emoji.y > 120) emoji.y = -20;
          return emoji;
      });
    }

    loop();

    return () => cancelAnimationFrame(frame);
  });

</script>

  <h1 class='main_title'>
    PMIRA-PE INCEPTION
    <p>42MADRID</p>
  </h1>
  
  <div>
    <button on:click={ e => menu = 0 }>Links</button>
    <button on:click={ e => menu = 1 }>Resumen</button>
    <button style="color:green" on:click={ e => menu = 2 }>Uranium fever</button>
  </div>

  {#if !menu}
  <div>
    <h3>Links</h3>
    <a href="/wp-login.php"><button>Wordpres login</button></a>
    <a href="/wordpress"><button>Wordpress</button></a>
    <button on:click={ e => alert("FTP no tiene una pagina como tal jeje")}>FTP</button>
    <a href="localhost:9000/"><button>Portainer</button></a>
    <a href="/adminer"><button>Adminer</button></a>
  </div>
  <div class="container">
    <img class="foto" alt="cibersecurity" src="/src/assets/ciberseguridad.jpeg"/>
    <div class="text-in-photo">pmira haciendo ciberseguridad</div>
  </div>
  
  {:else if menu == 1}
  <div class='text'>
    <h2>Resumen del proyecto</h2>
    <div class="columna1">
      <h3>Mandatory</h3>
      Este proyecto se compone de <b>3 servicios</b> básicos que son:
      <ol>
        <li>Nginx</li>
        <li>Wordpress</li>
        <li>MariaDB</li>
      </ol>
      <p>Cada servicio tiene que estar desplegado en un contenedor usando Docker Compose.</p>
      <p>De forma visual sería algo con este aspecto:</p>
      <img src="src/assets/mandatory.png" alt="mandatory diagram" width="400" height="400">
    
      <div>
        <h3>Nginx</h3>
        Es un servidor web que gestiona las peticiones http. Sirve para hacer tanto proxy inverso como equilibrador de cargas.
      </div>
      <div>
        <h3>Wordpress</h3>
        <img src="src/assets/wordpress.png" alt="wordpress logo" width="25">
        Es un sistema de gestión de contenidos enfocado a creación de páginas web. Basado en PHP.
      </div>
      <div>
        <h3>MariaDB</h3>
        <img src="src/assets/mariadb.png" alt="mariadb logo" width="100">
        Es un sistema de gestion de bases de datos sql. Derivado de MySQL, con algunas diferencias, se usan hasta los mismos comandos.
      </div>
    </div>
    
    <div class="columna2">
      <h3>Bonus</h3>
      En esta parte se añaden 5 contenedores con los siguientes servicios:
      <ol>
        <li>Redis cache</li>
        <li>FTP</li>
        <li>Static web</li>
        <li>Adminer</li>
        <li>Portainer</li>
      </ol>
      <img src="src/assets/bonus.png" alt="bonus esquema" width="700">
      <div>
        <h4>Static web</h4>
        Esta página es una web estática hecha con Svelte que es un framework de desarrollo front-end
      </div>
  
      <div>
        <h4>Redis</h4>
        <img src="src/assets/redis.png" alt="redis logo" width="50">
        es un motor de base de datos en memoria, basado en el almacenamiento en tablas de hashes
        pero que opcionalmente puede ser usada como una base de datos durable o persistente.
        Wordpress lo usa para almacenar query en cache, de esta forma las query son más rápidas.
      </div>
      
      <div>
        <h4>FTP</h4>
        <img src="src/assets/ftp.png" alt="ftp logo" width="50">
        Sus siglas significan <em>File Transfer Protocol</em>. Es un servicio que permite establecer
        una conexión dedicada a la transferencia de ficheros.
      </div>
      
      <div>
        <h4>Adminer</h4>
        Es una herramienta para administrar contenido en bases de datos.
      </div>
  
      <div>
        <h4>Portainer</h4>
        <img src="src/assets/portainer.png" alt="portainer logo" width="100">
          Este es un servicio para gestionar entornos de contenedores. Es decir, podremos gestionar mediante
          una interfaz los contenedores desplegados de nuestro docker compose mediante una url.
      </div>
    </div>

  </div>

  {:else}
  <div >
    <h2 style="color: green;">URANIUM FEVER ACTIVATED</h2>
    <img style="width: 50%;" alt="uranium fever" src="src/assets/fever.png"/>
    <audio autoplay><source src="src/assets/uranium.mp3" type="audio/mpeg"></audio>
    <button on:click={ e => menu = 0 }>Disconnect uranium fever</button>
    {#each confetti as c}
     <span style="color:rgb(21, 210, 15); left: {c.x}%; top: {c.y}%; transform: scale({c.r})">{c.character}</span>
    {/each}
  </div>
  {/if}
  
  <style>
    
  </style>

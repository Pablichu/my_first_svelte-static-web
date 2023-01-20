<script lang="ts">
  import { onMount } from 'svelte';

  let uranium_fever:boolean = false;
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

<main>
  <h1 class='main_title'>
    PMIRA-PE INCEPTION <p>42MADRID</p>
  </h1>

  <nav>
    <div style="position:relative">pmira-pe haciendo ciberseguridad</div>
    <img style="width: 200px;" alt="cibersecurity" src="/src/assets/ciberseguridad.jpeg"/>
  </nav>
  
  <h3>Resumen del proyecto</h3>
  
  <div>
    {#if !uranium_fever}
    <div class='button_explain'>
      <button>Wordpress</button>
      Aquí para ir al blog hecho con wordpress.
      <button>Wordpres login</button>
      Aquí para ir al login de wordpress.
    </div>

    <div class='button_explain'>
        <button on:click={ e => alert("Todavia no está hecho jeje")}>FTP</button>
        Aquí para ir al FTP.
        <p>
          Sus siglas significan <em>"File Transfer Protocol"</em>. Es un servicio que permite establecer
          una conexión dedicada a la transferencia de ficheros.
        </p>
    </div>

    <div class='button_explain'>
        <button on:click={ e => alert("Todavia no está hecho jeje")}>Portainer</button>
        Aquí para ir a Portainer.
        <p>
          Este es un servicio para gestionar entornos de contenedores. Es decir, podremos gestionar mediante
          una interfaz los contenedores desplegados de nuestro docker compose mediante una url.
        </p>
      </div>
      
    <div class='button_explain'>
      <button style="color:green" on:click={ e => uranium_fever = true }>Uranium fever</button>
    </div>
    {:else}
    <div class='button_explain'>
      <h2 style="color: green;">URANIUM FEVER ACTIVATED</h2>
      <button on:click={ e => uranium_fever = false }>Disconnect uranium fever</button>
      <p class="container">
        <iframe
          class="video"
          src="https://www.youtube.com/embed/GNkO2hzXluU?controls=0"
          title="Uranium fever my dude!!"
          frameborder="0"
          allowfullscreen>
        </iframe>
      </p>
      {#each confetti as c}
       <span style="color:rgb(21, 210, 15); left: {c.x}%; top: {c.y}%; transform: scale({c.r})">{c.character}</span>
      {/each}
    </div>
    {/if}
  </div>
</main>

<style>
  
  .main_title {
    font-family:Inter;
    font-size: 4em;
    COLOR: #ECA72C;
    text-shadow: 0px 0px 6px #ECA72C;
  }
  
  :global(body) {
    overflow: hidden;
  }
  
  span {
    position: absolute;
    font-size: 5vw;
    user-select: none;
  }
</style>
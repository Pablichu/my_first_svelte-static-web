<script lang="ts">
  import Youtube from "svelte-youtube";

  let uranium_fever:boolean = false;
  const videoId = "GNkO2hzXluU"

  function onReady(event) {
    // access to player in all event handlers via event.target
    event.target.playVideo();
  }

</script>

<main>
  <h1 class='main_title'>
    PMIRA-PE INCEPTION <p>42MADRID</p>
  </h1>

  
  
  <body>
    <h3>Titulo</h3>
    explicasao
  
    <div>
      <div class='button_explain'>
        Que pasa tú?
          <button>Wordpress</button>
      </div>

      <div class='button_explain'>
          <button>Wordpres login</button>
      </div>

      <div class='button_explain'>
          <button on:click={ e => alert("Todavia no está hecho jeje")}>Futuro FTP</button>
      </div>

      <div class='button_explain'>
          <button on:click={ e => alert("Todavia no está hecho jeje")}>Futuro portainer</button>
      </div>

      <div class='button_explain'>
        {#if !uranium_fever}
            <button style="color:green" on:click={ e => uranium_fever = true }>Uranium fever</button>
        {:else}
          <h2 style="color: green;">URANIUM FEVER ACTIVATED</h2>
          <p class="container">
            <iframe
              class="video"
              src="https://www.youtube.com/embed/GNkO2hzXluU?controls=0"
              title="Uranium fever my dude!!"
              frameborder="0"
              allowfullscreen>
            </iframe>
          </p>
          <button on:click={ e => uranium_fever = false }>Disconnect uranium fever</button>
        {/if}
      </div>
    </div>
  </body>
</main>

<style>
  
  .main_title {
    font-family:Inter;
    font-size: 4em;
    COLOR: #ECA72C;
    text-shadow: 0px 0px 6px #ECA72C;
  }

  .button_explain {
    display: block;
    padding: 1em;
    color: aliceblue;
  }

</style>

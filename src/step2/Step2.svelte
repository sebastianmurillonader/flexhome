<!-- Test 20210218 -->
<script>
  // Svelte
  import { fade } from "svelte/transition";

  // Stores
  import { fetchedFraccionamientos } from "../msf-stores";

  // Components
  import Loader from "../components/Loader.svelte";
  import Fraccionamientos from "./Fraccionamientos.svelte";
  import ErrorMessage from "../components/ErrorMessage.svelte";

  // Exports
  export let name;
</script>

<div class="msf-content" in:fade={{ duration: 250 }}>

  <!-- Header -->
  <div class="msf-header">
    <h2 class="msf-title">Selecciona el desarrollo</h2>
    <p>¡Tenemos residencias disponibles en cada uno de ellos!</p>
  </div>

  <!-- Fraccionamientos -->
  {#await $fetchedFraccionamientos}
    <Loader />
  {:then fraccionamientos}
    <Fraccionamientos {name} {fraccionamientos} on:select />
  {:catch error}
    <ErrorMessage />
  {/await}

</div>

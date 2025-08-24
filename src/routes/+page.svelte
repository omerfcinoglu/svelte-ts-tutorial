<script lang="ts">
  import { fade } from "svelte/transition";
  import Page1 from "$lib/pages/Page1.svelte";
  import Page2 from "$lib/pages/Page2.svelte";
  import Page3 from "$lib/pages/Page3.svelte";
  import Page4 from "$lib/pages/Page4.svelte";

  let currentPage = 0;
  const totalPages = 4;

  let isAnimating = false;
  const animationDuration = 1200;

  function handleWheel(event: WheelEvent) {
    if (isAnimating) return;

    if (event.deltaY > 0 && currentPage < totalPages - 1) {
      goToPage(currentPage + 1);
    } else if (event.deltaY < 0 && currentPage > 0) {
      goToPage(currentPage - 1);
    }
  }

  function goToPage(page: number) {
    isAnimating = true;
    currentPage = page;
    setTimeout(() => (isAnimating = false), animationDuration);
  }
</script>

<div class="container" on:wheel={handleWheel}>
  {#key currentPage}
    <div transition:fade={{ duration: 800 }}>
      {#if currentPage === 0}
        <Page1 />
      {:else if currentPage === 1}
        <Page2 />
      {:else if currentPage === 2}
        <Page3 />
      {:else if currentPage === 3}
        <Page4 />
      {/if}
    </div>
  {/key}
</div>

<style>
  .container {
    width: 100vw;
    height: 100vh;
    overflow: hidden;
    font-family: sans-serif;
  }
</style>

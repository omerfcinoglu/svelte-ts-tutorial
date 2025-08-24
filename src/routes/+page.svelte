<script lang="ts">
  import { fly, fade } from "svelte/transition";
  import { cubicOut } from "svelte/easing";

  let currentPage = 0;
  const totalPages = 4;

  let isAnimating = false;
  const animationDuration = 1200; // ms

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

    setTimeout(() => {
      isAnimating = false;
    }, animationDuration);
  }

  const titles = ["Page 1", "Page 2", "Page 3", "Page 4"];
</script>

<div class="container" on:wheel={handleWheel}>
  {#if currentPage === 0}
    <div class="page">
      <div class="shapes">
        <div class="square" in:fly={{ y: -50, duration: 600 }}></div>
        <div
          class="triangle"
          in:fly={{ y: 50, duration: 600, delay: 200 }}
        ></div>
        <div class="circle" in:fly={{ x: 50, duration: 600, delay: 400 }}></div>
      </div>
      <h1 in:fade={{ duration: 1000, easing: cubicOut }}>
        {titles[0]}
      </h1>
    </div>
  {/if}

  {#if currentPage === 1}
    <div class="page">
      <div class="shapes">
        <div class="circle" in:fly={{ x: -50, duration: 600 }}></div>
        <div
          class="square"
          in:fly={{ y: -50, duration: 600, delay: 200 }}
        ></div>
        <div
          class="triangle"
          in:fly={{ y: 50, duration: 600, delay: 400 }}
        ></div>
      </div>
      <h1 in:fade={{ duration: 1000 }}>{titles[1]}</h1>
    </div>
  {/if}

  {#if currentPage === 2}
    <div class="page">
      <div class="shapes">
        <div class="triangle" in:fly={{ y: -50, duration: 600 }}></div>
        <div class="circle" in:fly={{ x: 50, duration: 600, delay: 200 }}></div>
        <div class="square" in:fly={{ y: 50, duration: 600, delay: 400 }}></div>
      </div>
      <h1 in:fade={{ duration: 1000 }}>{titles[2]}</h1>
    </div>
  {/if}

  {#if currentPage === 3}
    <div class="page">
      <div class="shapes">
        <div class="square" in:fly={{ y: 50, duration: 600 }}></div>
        <div
          class="triangle"
          in:fly={{ x: -50, duration: 600, delay: 200 }}
        ></div>
        <div
          class="circle"
          in:fly={{ y: -50, duration: 600, delay: 400 }}
        ></div>
      </div>
      <h1 in:fade={{ duration: 1000 }}>{titles[3]}</h1>
    </div>
  {/if}
</div>

<style>
  .container {
    width: 100vw;
    height: 100vh;
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
    background: #111;
    color: white;
    font-family: sans-serif;
  }

  .page {
    width: 100vw;
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .shapes {
    display: flex;
    gap: 20px;
    margin-bottom: 30px;
  }

  .square {
    width: 40px;
    height: 40px;
    background: crimson;
  }
  .triangle {
    width: 0;
    height: 0;
    border-left: 25px solid transparent;
    border-right: 25px solid transparent;
    border-bottom: 40px solid dodgerblue;
  }
  .circle {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background: limegreen;
  }

  h1 {
    font-size: 3rem;
    font-weight: bold;
    margin: 0;
  }
</style>

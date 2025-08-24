<script lang="ts">
  import { fly, fade } from "svelte/transition";

  const hearts = Array.from({ length: 6 }, (_, i) => i);
</script>

<div class="page">
  <h1 in:fade={{ duration: 1000 }}>👋 Greetings, welcome!</h1>

  {#each hearts as h, i}
    <div
      class="heart"
      style="left: {20 + i * 15}%; animation-delay: {i * 0.6}s"
    >
      ❤️
    </div>
  {/each}
</div>

<style>
  .page {
    width: 100vw;
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    position: relative;
  }

  h1 {
    font-size: 3rem;
    font-weight: bold;
    margin-bottom: 2rem;
  }

  .heart {
    position: absolute;
    bottom: 0;
    font-size: 2rem;
    color: crimson;
    animation: floatUp 4s linear forwards;
    opacity: 0.8;
  }

  @keyframes floatUp {
    0% {
      transform: translateY(0);
      opacity: 0.9;
    }
    50% {
      opacity: 0.6;
    }
    100% {
      transform: translateY(-100vh);
      opacity: 0;
    }
  }
</style>

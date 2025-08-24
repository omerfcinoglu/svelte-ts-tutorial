<script lang="ts">
  import { fade } from "svelte/transition";

  const hearts = Array.from({ length: 9 }, (_, i) => ({
    id: i,
    left: 40 + Math.random() * 20,
    drift: (Math.random() - 0.5) * 250,
  }));
</script>

<div class="page">
  <h1 transition:fade={{ duration: 1000 }}>👋 Greetings!</h1>

  {#each hearts as heart, i}
    <div
      class="heart"
      style="
        left: {heart.left}%;
        animation-delay: {i * 0.01}s;
        --drift: {heart.drift}px;
      "
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
    background: #111;
    color: white;
  }

  h1 {
    font-size: 3rem;
    font-weight: bold;
    margin-bottom: 2rem;
  }

  .heart {
    position: absolute;
    bottom: 0;
    font-size: 5rem;
    color: crimson;
    animation: floatUp 4s ease-out forwards;
  }

  @keyframes floatUp {
    0% {
      transform: translateY(0) translateX(0);
      opacity: 1;
    }
    50% {
      opacity: 0.7;
    }
    100% {
      transform: translateY(-100vh) translateX(var(--drift));
      opacity: 0;
    }
  }
</style>

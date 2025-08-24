<script lang="ts">
  const hearts = Array.from({ length: 9 }, (_, i) => ({
    id: i,
    left: 40 + Math.random() * 20,
    drift: (Math.random() - 0.5) * 250,
  }));
</script>

<div class="page1">
  <h1 class="title">👋 Greetings, welcome!</h1>

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
  .page1 {
    width: 100vw;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
  }
  .title {
    font-size: 3rem;
    font-weight: 700;
    margin: 0 0 2rem 0;
    animation: titleIn 900ms ease-out both;
  }
  @keyframes titleIn {
    from {
      opacity: 0;
      transform: translateY(12px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  .heart {
    position: absolute;
    bottom: 0;
    font-size: 2rem;
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

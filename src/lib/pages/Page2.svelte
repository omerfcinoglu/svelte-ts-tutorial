<script lang="ts">
  import { fly } from "svelte/transition";
  let active = false;

  function inView(node: HTMLElement) {
    const io = new IntersectionObserver(
      ([e]) => {
        active = e.isIntersecting && e.intersectionRatio >= 0.6;
      },
      { threshold: [0, 0.25, 0.5, 0.6, 0.75, 1] }
    );
    io.observe(node);
    return {
      destroy() {
        io.disconnect();
      },
    };
  }
</script>

<div class="page" use:inView>
  {#key active}
    {#if active}
      <div class="card" transition:fly={{ y: 80, duration: 800 }}>
        <h2>Welcome to our wedding!</h2>
      </div>

      <div class="circle left"></div>
      <div class="circle right"></div>
    {/if}
  {/key}
</div>

<style>
  .page {
    width: 100vw;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    background: #222;
    color: white;
    overflow: hidden;
  }

  .card {
    background: white;
    color: #222;
    padding: 2rem 3rem;
    border-radius: 12px;
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.25);
    z-index: 2;
    height: 150px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  h2 {
    margin: 0;
    font-size: 1.8rem;
  }

  .circle {
    position: absolute;
    width: 80px;
    height: 80px;
    border-radius: 50%;
    background: crimson;
    top: 50%;
    transform: translateY(-50%);
    z-index: 1;
    opacity: 0.9;
    animation-duration: 1.5s;
    animation-timing-function: ease;
    animation-fill-mode: forwards;
  }

  .left {
    top: 40%;
    left: -1vw;
    animation-name: moveInLeft;
    animation-delay: 0.2s;
  }
  .right {
    top: 60%;
    right: -1vw;
    animation-name: moveInRight;
    animation-delay: 0.4s;
  }

  @keyframes moveInLeft {
    to {
      transform: translateY(-50%) translateX(20vw);
    }
  }
  @keyframes moveInRight {
    to {
      transform: translateY(-50%) translateX(-20vw);
    }
  }
</style>

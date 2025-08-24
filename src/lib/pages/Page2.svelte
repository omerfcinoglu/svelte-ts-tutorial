<script lang="ts">
  import { fly } from "svelte/transition";
</script>

<div class="page">
  <div class="card" transition:fly={{ y: 80, duration: 800 }}>
    <h2>Welcome to our wedding!</h2>
  </div>

  <div class="circle left"></div>
  <div class="circle right"></div>
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
    animation: moveIn 1.5s ease forwards;
    opacity: 0.8;
  }

  .circle.left {
    left: -120px;
    animation-delay: 0.2s;
  }

  .circle.right {
    right: -120px;
    animation-delay: 0.4s;
    animation-name: moveInRight;
  }

  @keyframes moveIn {
    to {
      transform: translateY(-50%) translateX(100px);
    }
  }

  @keyframes moveInRight {
    to {
      transform: translateY(-50%) translateX(-100px);
    }
  }
</style>

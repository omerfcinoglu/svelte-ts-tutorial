<script lang="ts">
  export let title = "";
  export let text = "";
</script>

<div class="card">
  <h3>{title}</h3>
  <p>{text}</p>
</div>

<style>
  .card {
    background: rgba(255, 255, 255, 0.08);
    border: 1px solid rgba(255, 255, 255, 0.15);
    border-radius: 16px;
    padding: 1.4rem;
    backdrop-filter: blur(6px);
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.25);
    transform: translateY(16px) scale(0.98);
    opacity: 0;
    animation: enter 0.8s ease forwards;
    transition:
      transform 0.25s ease,
      box-shadow 0.25s ease;
  }
  .card:hover {
    transform: translateY(8px) scale(1.01);
    box-shadow: 0 18px 40px rgba(0, 0, 0, 0.35);
  }
  h3 {
    margin: 0 0 0.5rem 0;
    font-size: 1.25rem;
  }
  p {
    margin: 0;
    line-height: 1.4;
    color: #dbdde2;
  }
  @keyframes enter {
    from {
      opacity: 0;
      transform: translateY(24px) scale(0.95);
    }
    to {
      opacity: 1;
      transform: translateY(16px) scale(0.98);
    }
  }
</style>

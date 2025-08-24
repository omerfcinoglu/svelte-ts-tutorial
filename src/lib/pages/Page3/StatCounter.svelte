<script lang="ts">
  import { onMount } from "svelte";
  export let label = "";
  export let to = 100;
  export let duration = 1200;
  let value = 0;
  onMount(() => {
    const start = performance.now();
    function step(t: number) {
      const p = Math.min(1, (t - start) / duration);
      value = Math.floor(to * (1 - Math.pow(1 - p, 3)));
      if (p < 1) requestAnimationFrame(step);
    }
    requestAnimationFrame(step);
  });
</script>

<div class="stat">
  <div class="num">{value}</div>
  <div class="lab">{label}</div>
</div>

<style>
  .stat {
    text-align: center;
  }
  .num {
    font-size: 2rem;
    font-weight: 800;
  }
  .lab {
    opacity: 0.8;
  }
</style>

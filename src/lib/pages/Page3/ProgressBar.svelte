<script lang="ts">
  import { onMount } from "svelte";
  export let percent = 70;
  export let duration = 1000;
  let w = 0;
  onMount(() => {
    const start = performance.now();
    function step(t: number) {
      const p = Math.min(1, (t - start) / duration);
      w = percent * p;
      if (p < 1) requestAnimationFrame(step);
    }
    requestAnimationFrame(step);
  });
</script>

<div class="wrap">
  <div class="bar" style="width: {w}%"></div>
</div>

<style>
  .wrap {
    width: 100%;
    height: 10px;
    background: rgba(255, 255, 255, 0.15);
    border-radius: 999px;
    overflow: hidden;
  }
  .bar {
    height: 100%;
    background: linear-gradient(90deg, #7aa2ff, #9b59ff);
    border-radius: 999px;
  }
</style>

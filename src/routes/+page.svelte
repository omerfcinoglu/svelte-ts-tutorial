<script lang="ts">
  import Page1 from "$lib/pages/Page1.svelte";
  import Page2 from "$lib/pages/Page2.svelte";
  import { Fullpage, FullpageSection, FullpageSlide } from "svelte-fullpage";
</script>

<Fullpage class="fp">
  <FullpageSection class="page bg1" title="Home"><Page1 /></FullpageSection>
  <FullpageSection class="page bg3" title="Present"><Page2 /></FullpageSection>
  <FullpageSection class="page bg4" title="Future">Future</FullpageSection>
</Fullpage>

<style>
  :global(html, body) {
    margin: 0;
    height: 100%;
  }
</style>

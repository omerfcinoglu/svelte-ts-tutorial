<script lang="ts">
  import Page1 from "$lib/pages/Page1.svelte";
  import { Fullpage, FullpageSection, FullpageSlide } from "svelte-fullpage";
</script>

<Fullpage class="fp">
  <FullpageSection class="page bg1" title="Home">Home content</FullpageSection>

  <FullpageSection class="page bg2" title="History">
    <FullpageSlide class="page" title="1982-1993"><Page1 /></FullpageSlide>
    <FullpageSlide class="page" title="1993-2006">Slide B</FullpageSlide>
    <FullpageSlide class="page" title="2006-present">Slide C</FullpageSlide>
  </FullpageSection>

  <FullpageSection class="page bg3" title="Present">Present</FullpageSection>
  <FullpageSection class="page bg4" title="Future">Future</FullpageSection>
</Fullpage>

<style>
  :global(html, body) {
    margin: 0;
    height: 100%;
  }
  .fp {
    width: 100vw;
    height: 100vh;
    overflow: hidden;
  }
  .page {
    width: 100vw;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .bg1 {
    background: #111;
    color: #fff;
  }
  .bg2 {
    background: #222;
    color: #fff;
  }
  .bg3 {
    background: #f5f5f5;
    color: #111;
  }
  .bg4 {
    background: #0a3d62;
    color: #fff;
  }
</style>

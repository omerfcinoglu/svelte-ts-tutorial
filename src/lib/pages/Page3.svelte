<script lang="ts">
  import FancyCard from "./Page3/FancyCard.svelte";
  import ProgressBar from "./Page3/ProgressBar.svelte";
  import StatCounter from "./Page3/StatCounter.svelte";

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

  const features = [
    {
      title: "Smooth Transitions",
      text: "Fly, fade, keyframes ve parallax birleşimi.",
    },
    { title: "Interactive Cards", text: "Hover ile ince ölçek ve gölge." },
    { title: "Live Metrics", text: "Girişte sayan sayaç ve ilerleme." },
  ];
</script>

<div class="page3" use:inView>
  {#key active}
    {#if active}
      <div class="decor a"></div>
      <div class="decor b"></div>
      <div class="decor c"></div>

      <section class="hero">
        <h1 class="title">Effects & Motion Lab</h1>
        <p class="subtitle">Page 3 • Motion, counters, parallax, progress</p>
      </section>

      <section class="cards">
        {#each features as f, i}
          <div class="cardWrap" style="animation-delay: {i * 120}ms">
            <FancyCard title={f.title} text={f.text} />
          </div>
        {/each}
      </section>

      <section class="stats">
        <StatCounter label="Visitors" to={1280} duration={1200} />
        <StatCounter label="Hearts" to={342} duration={1200} />
        <StatCounter label="Stars" to={89} duration={1200} />
      </section>

      <section class="progress">
        <div class="row">
          <span>Setup</span>
          <ProgressBar percent={100} duration={900} />
        </div>
        <div class="row">
          <span>Design</span>
          <ProgressBar percent={80} duration={1100} />
        </div>
        <div class="row">
          <span>Polish</span>
          <ProgressBar percent={55} duration={1300} />
        </div>
      </section>

      <section class="cta">
        <button class="btn">Continue</button>
      </section>
    {/if}
  {/key}
</div>

<style>
  .page3 {
    width: 100vw;
    height: 100vh;
    position: relative;
    color: #fff;
    background: radial-gradient(
        80vmax 80vmax at 10% 10%,
        rgba(123, 104, 238, 0.25),
        transparent 60%
      ),
      radial-gradient(
        60vmax 60vmax at 90% 20%,
        rgba(72, 61, 139, 0.25),
        transparent 60%
      ),
      linear-gradient(180deg, #10131a, #0d0f15);
    display: grid;
    grid-template-rows: auto auto auto auto 1fr;
    padding: 6vh 6vw;
    overflow: hidden;
  }

  .decor {
    position: absolute;
    border-radius: 50%;
    filter: blur(30px);
    opacity: 0.22;
    animation: float 12s ease-in-out infinite alternate;
  }
  .decor.a {
    width: 220px;
    height: 220px;
    background: #7aa2ff;
    top: 8%;
    left: 4%;
    animation-delay: 0.2s;
  }
  .decor.b {
    width: 180px;
    height: 180px;
    background: #9b59ff;
    top: 20%;
    right: 8%;
    animation-delay: 0.6s;
  }
  .decor.c {
    width: 260px;
    height: 260px;
    background: #1abc9c;
    bottom: -6%;
    left: 22%;
    animation-delay: 1s;
  }
  @keyframes float {
    from {
      transform: translateY(0) translateX(0);
    }
    to {
      transform: translateY(-20px) translateX(12px);
    }
  }

  .hero {
    text-align: center;
    margin-bottom: 2vh;
  }
  .title {
    margin: 0;
    font-size: clamp(2rem, 4vw, 3.4rem);
    letter-spacing: 0.5px;
    animation: titleIn 700ms ease both;
  }
  .subtitle {
    margin: 0.6rem 0 0 0;
    opacity: 0.85;
    animation: fadeIn 900ms ease both 0.15s;
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
  @keyframes fadeIn {
    from {
      opacity: 0;
    }
    to {
      opacity: 1;
    }
  }

  .cards {
    display: grid;
    grid-template-columns: repeat(3, minmax(200px, 1fr));
    gap: 1.2rem;
    margin: 2vh 0 3vh 0;
  }
  .cardWrap {
    opacity: 0;
    animation: rise 0.6s ease forwards;
  }
  @keyframes rise {
    from {
      opacity: 0;
      transform: translateY(18px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  .stats {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.2rem;
    align-items: center;
    justify-items: center;
    margin-bottom: 2vh;
  }

  .progress {
    display: grid;
    gap: 0.9rem;
  }
  .row {
    display: grid;
    grid-template-columns: 120px 1fr;
    gap: 1rem;
    align-items: center;
  }
  .row span {
    opacity: 0.9;
  }

  .cta {
    display: grid;
    place-items: center;
  }
  .btn {
    padding: 0.9rem 1.4rem;
    border: none;
    border-radius: 12px;
    background: linear-gradient(135deg, #7aa2ff, #9b59ff);
    color: #fff;
    font-weight: 700;
    letter-spacing: 0.3px;
    cursor: pointer;
    box-shadow: 0 10px 28px rgba(0, 0, 0, 0.3);
    transition:
      transform 0.2s ease,
      box-shadow 0.2s ease,
      filter 0.2s ease;
  }
  .btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 14px 36px rgba(0, 0, 0, 0.35);
    filter: saturate(1.1);
  }

  @media (max-width: 900px) {
    .cards {
      grid-template-columns: 1fr;
    }
    .stats {
      grid-template-columns: 1fr 1fr;
    }
  }
</style>

<script>
  // Unlisted page: not in the nav, footer, or robots.txt, and marked noindex.
  // Reachable only by typing luminaryrobotics.org/scorer.

  // Placeholder store links. Swap in the real URLs once the listings are live.
  const APP_STORE_URL = '';
  const GOOGLE_PLAY_URL = '';

  const screens = [
    { name: 'home', title: 'Home', desc: 'Start a game in one tap.' },
    { name: 'timer', title: 'Timer', desc: 'Auto, transition, and TeleOp with field sounds.' },
    { name: 'calculator', title: 'Calculator', desc: 'Add up a score after the match.' },
    { name: 'analysis', title: 'Analysis', desc: 'Saved matches and charts over time.' },
  ];

  function placeholder(event, url) {
    if (!url) event.preventDefault();
  }
</script>

<svelte:head>
  <title>BioBuzz Scorer | Luminary Robotics FTC 36633</title>
  <meta name="robots" content="noindex, nofollow" />
  <meta name="description" content="BioBuzz Scorer, a scoring app for the FIRST Tech Challenge BIOBUZZ season, made by FTC Team 36633." />
</svelte:head>

{#snippet shot(name, alt, loading)}
  <img class="shot" src="/images/scorer/{name}.png" {alt} width="1600" height="783" {loading} />
{/snippet}

{#snippet storeButtons()}
  <div class="stores">
    <a
      href={APP_STORE_URL || '#'}
      class="store"
      aria-label="Download on the App Store"
      onclick={(e) => placeholder(e, APP_STORE_URL)}
    >
      <svg class="store__icon" viewBox="0 0 24 24" aria-hidden="true">
        <path
          fill="currentColor"
          d="M12.152 6.896c-.948 0-2.415-1.078-3.96-1.04-2.04.027-3.91 1.183-4.961 3.014-2.117 3.675-.546 9.103 1.519 12.09 1.013 1.454 2.208 3.09 3.792 3.039 1.52-.065 2.09-.987 3.935-.987 1.831 0 2.35.987 3.96.948 1.637-.026 2.676-1.48 3.676-2.948 1.156-1.688 1.636-3.325 1.662-3.415-.039-.013-3.182-1.221-3.22-4.857-.026-3.04 2.48-4.494 2.597-4.559-1.429-2.09-3.623-2.324-4.39-2.376-2-.156-3.675 1.09-4.61 1.09zM15.53 3.83c.843-1.012 1.4-2.427 1.245-3.83-1.207.052-2.662.805-3.532 1.818-.78.896-1.454 2.338-1.273 3.714 1.338.104 2.715-.688 3.559-1.701"
        />
      </svg>
      <span class="store__text">
        <span class="store__small">Download on the</span>
        <span class="store__big">App Store</span>
      </span>
    </a>

    <a
      href={GOOGLE_PLAY_URL || '#'}
      class="store"
      aria-label="Get it on Google Play"
      onclick={(e) => placeholder(e, GOOGLE_PLAY_URL)}
    >
      <svg class="store__icon store__icon--android" viewBox="0 0 24 24" aria-hidden="true">
        <path
          fill="currentColor"
          fill-rule="evenodd"
          d="M1.5 19a10.5 10.5 0 0 1 21 0zM6.4 14.6a1.15 1.15 0 1 0 2.3 0a1.15 1.15 0 1 0 -2.3 0zM15.3 14.6a1.15 1.15 0 1 0 2.3 0a1.15 1.15 0 1 0 -2.3 0z"
        />
        <path
          stroke="currentColor"
          stroke-width="1.3"
          stroke-linecap="round"
          fill="none"
          d="M6.2 10.2 4.2 6.8M17.8 10.2l2-3.4"
        />
      </svg>
      <span class="store__text">
        <span class="store__small">Get it on</span>
        <span class="store__big">Google Play</span>
      </span>
    </a>
  </div>
{/snippet}

<!-- ── Hero ─────────────────────────────────────────────────── -->
<section class="hero">
  <div class="hero__inner container">
    <div class="hero__content">
      <h1 class="hero__title">BioBuzz Scorer</h1>
      <p class="hero__intro">Easily score matches on your phone.</p>
      {@render storeButtons()}
    </div>
    <div class="hero__visual">
      {@render shot('board', 'The BioBuzz Scorer scoring board', 'eager')}
    </div>
  </div>
</section>

<!-- ── Screens ──────────────────────────────────────────────── -->
<section class="section">
  <div class="container">
    <div class="screens">
      {#each screens as screen}
        <figure class="screen">
          {@render shot(screen.name, `BioBuzz Scorer ${screen.title} screen`, 'lazy')}
          <figcaption>
            <span class="screen__title">{screen.title}</span>
            <span class="screen__desc">{screen.desc}</span>
          </figcaption>
        </figure>
      {/each}
    </div>
  </div>
</section>

<!-- ── Download ─────────────────────────────────────────────── -->
<section class="section--sm download">
  <div class="container">
    {@render storeButtons()}
    <p class="legal">
      <em>FIRST</em>®, <em>FIRST</em>® Tech Challenge, FTC®, BIOBUZZ™, and all accompanying
      logos are trademarks of For Inspiration and Recognition of Science and Technology
      (<em>FIRST</em>®). Used by special permission of <em>FIRST</em>, which is not overseeing,
      involved with, or responsible for this product. RTX and the RTX logo are trademarks of
      RTX Corporation. Apple and the App Store are trademarks of Apple Inc. Google Play and
      Android are trademarks of Google LLC.
    </p>
  </div>
</section>

<style>
  /* ── Hero ─────────────────────────────────── */
  .hero {
    display: flex;
    align-items: center;
    min-height: 88vh;
    padding-top: var(--nav-h);
  }

  .hero__inner {
    display: grid;
    grid-template-columns: 5fr 7fr;
    gap: var(--space-8);
    align-items: center;
    padding-top: var(--space-8);
    padding-bottom: var(--space-8);
  }

  .hero__title {
    font-family: var(--font-heading);
    font-size: clamp(2.5rem, 5vw, var(--text-5xl));
    font-weight: 700;
    letter-spacing: -0.03em;
    line-height: 1;
    color: var(--text);
    margin-bottom: var(--space-5);
  }

  .hero__intro {
    font-size: var(--text-md);
    color: var(--text-2);
    line-height: 1.7;
    max-width: 440px;
    margin-bottom: var(--space-7);
  }

  /* ── Store buttons ────────────────────────── */
  .stores {
    display: flex;
    gap: var(--space-3);
    flex-wrap: wrap;
  }

  .store {
    display: inline-flex;
    align-items: center;
    gap: var(--space-3);
    min-width: 168px;
    padding: 10px 20px 10px 16px;
    background: var(--btn-bg);
    color: var(--btn-text);
    border: 1px solid var(--btn-border);
    border-radius: 10px;
    transition: opacity var(--transition), transform var(--transition);
  }

  .store:hover { opacity: 0.85; }
  .store:active { transform: scale(0.98); }

  .store__icon {
    width: 26px;
    height: 26px;
    flex-shrink: 0;
  }

  .store__text {
    display: flex;
    flex-direction: column;
    line-height: 1.15;
  }

  .store__small {
    font-size: 0.6875rem;
    letter-spacing: 0.02em;
  }

  .store__big {
    font-size: 1.25rem;
    font-weight: 700;
    letter-spacing: -0.01em;
  }

  .store__icon--android { color: #3ddc84; }

  /* ── Screenshots ──────────────────────────── */
  .shot {
    width: 100%;
    height: auto;
    filter: drop-shadow(0 18px 30px rgba(0, 0, 0, 0.18));
  }

  .screens {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: var(--space-9) var(--space-7);
  }

  .screen { margin: 0; }

  .screen figcaption {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: var(--space-1);
    margin-top: var(--space-5);
    text-align: center;
  }

  .screen__title {
    font-size: var(--text-lg);
    font-weight: 700;
    color: var(--text);
  }

  .screen__desc {
    font-size: var(--text-sm);
    color: var(--text-2);
  }

  /* ── Download ─────────────────────────────── */
  .download { padding-bottom: var(--space-10); }

  .download .stores { justify-content: center; }


  .legal {
    margin: var(--space-8) auto 0;
    text-align: center;
    font-size: var(--text-xs);
    color: var(--text-3);
    line-height: 1.6;
    max-width: 820px;
  }

  .legal em { font-style: italic; }

  /* ── Responsive ───────────────────────────── */
  @media (max-width: 900px) {
    .hero { min-height: auto; }
    .hero__inner { grid-template-columns: 1fr; gap: var(--space-7); }
  }

  @media (max-width: 600px) {
    .screens { grid-template-columns: 1fr; gap: var(--space-8); }
  }
</style>

<script lang="ts">
  import ServerStatus from "$lib/components/ServerStatus.svelte";
  import HowToConnect from "$lib/components/HowToConnect.svelte";
  import DynmapSection from "$lib/components/DynmapSection.svelte";
  import { base } from "$app/paths";

  const serverAddress = "mc.lekkerboys.co.za";

  let copiedIp = $state(false);

  async function copyIp() {
    try {
      await navigator.clipboard.writeText(serverAddress);
      copiedIp = true;
      setTimeout(() => (copiedIp = false), 2500);
    } catch {
      // silently fail
    }
  }
</script>

<svelte:head>
  <title>LEKKERBOYS — SMP Live, Modded Coming Soon</title>
  <meta
    name="description"
    content="LEKKERBOYS runs a live cross-platform SMP now, with a modded server coming soon."
  />
</svelte:head>

<!-- ======================== HERO SECTION ======================== -->
<section
  id="home"
  class="relative min-h-[78svh] sm:min-h-[84svh] flex items-center justify-center overflow-hidden pt-32 sm:pt-28 pb-8"
>
  <div class="absolute inset-0">
    <img
      src={`${base}/images/hero-bg.webp`}
      alt="LEKKERBOYS Minecraft Landscape"
      class="w-full h-full object-cover object-center"
    />
    <div
      class="absolute inset-0 bg-gradient-to-b from-surface-primary/60 via-surface-primary/30 to-surface-primary"
    ></div>
    <div
      class="absolute inset-0 bg-gradient-to-r from-surface-primary/50 via-transparent to-surface-primary/50"
    ></div>
    <div
      class="absolute inset-0 opacity-[0.03]"
      style="background-image: url('data:image/svg+xml,%3Csvg viewBox=%220 0 256 256%22 xmlns=%22http://www.w3.org/2000/svg%22%3E%3Cfilter id=%22n%22%3E%3CfeTurbulence type=%22fractalNoise%22 baseFrequency=%220.9%22 numOctaves=%224%22 stitchTiles=%22stitch%22/%3E%3C/filter%3E%3Crect width=%22100%25%22 height=%22100%25%22 filter=%22url(%23n)%22/%3E%3C/svg%3E');"
    ></div>
  </div>

  <div class="relative z-10 px-4 sm:px-6 max-w-6xl mx-auto w-full">
    <div class="text-center max-w-4xl mx-auto">
      <div class="mb-5 animate-fade-in-up" style="animation-delay: 0.1s">
        <span
          class="inline-flex items-center gap-2 px-4 py-2 rounded-full
                 bg-green-500/10 border border-green-500/20 text-green-300
                 text-xs font-medium tracking-wider uppercase"
        >
          <span class="w-2 h-2 rounded-full bg-green-400 animate-pulse"></span>
          Two Servers, One Crew
        </span>
      </div>

      <h1 class="animate-fade-in-up" style="animation-delay: 0.2s">
        <span
          class="block font-pixel text-[2.8rem] leading-[0.92] sm:text-6xl md:text-7xl lg:text-8xl text-cream
                 drop-shadow-[0_4px_0_rgba(0,0,0,0.8)] tracking-[0.01em] sm:tracking-wider mb-5 sm:mb-3"
          style="text-shadow: 0 0 40px rgba(92, 180, 60, 0.2), 0 4px 0 rgba(0,0,0,0.6), 0 8px 20px rgba(0,0,0,0.4);"
        >
          <span class="sm:hidden leading-[1.08]">
            <span class="block mb-3">LEKKER</span>
            <span class="block">BOYS</span>
          </span>
          <span class="hidden sm:block">LEKKERBOYS</span>
        </span>
      </h1>

      <p
        class="text-[1.05rem] sm:text-xl text-cream-muted/80 max-w-2xl mx-auto mb-7 leading-relaxed
               animate-fade-in-up"
        style="animation-delay: 0.35s"
      >
        Join the live cross-platform SMP now and keep an eye on the modded
        server that is coming soon.
      </p>

      <div
        class="mb-8 flex flex-col sm:flex-row items-center justify-center gap-3 sm:gap-4
               animate-fade-in-up"
        style="animation-delay: 0.5s"
      >
        <button
          onclick={copyIp}
          class="group inline-flex w-auto items-center justify-center gap-3 px-4 sm:px-5 py-4 sm:py-3 rounded-xl
                 bg-green-400 hover:bg-green-300 text-surface-primary
                 font-bold text-base transition-all duration-300
                 shadow-[0_0_20px_rgba(92,180,60,0.18)] hover:shadow-[0_0_30px_rgba(92,180,60,0.28)]
                 active:scale-[0.98]"
        >
          {#if copiedIp}
            <svg
              class="w-5 h-5"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
              stroke-width="2.5"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M4.5 12.75l6 6 9-13.5"
              />
            </svg>
            <span>IP Copied</span>
          {:else}
            <svg
              class="w-5 h-5"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
              stroke-width="2"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M5.25 8.25h15m-16.5 7.5h15m-1.8-13.5l-3.9 19.5m-2.1-19.5l-3.9 19.5"
              />
            </svg>
            <span>Copy IP</span>
            <span class="text-surface-primary/45">&mdash;</span>
            <span
              class="text-sm font-normal text-surface-primary/65 whitespace-nowrap"
            >
              {serverAddress}
            </span>
          {/if}
        </button>

        <a
          href="#servers"
          class="inline-flex w-auto items-center justify-center gap-2 px-4 sm:px-5 py-4 sm:py-3 rounded-xl
                 bg-cream/5 hover:bg-cream/10 text-cream border border-cream/10
                 hover:border-cream/25 font-medium text-base transition-all duration-300
                 active:scale-[0.98] backdrop-blur-sm"
        >
          <svg
            class="w-5 h-5"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            stroke-width="1.5"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5"
            />
          </svg>
          View Both Servers
        </a>
      </div>
    </div>

    <div
      class="mt-20 mb-14 grid grid-cols-1 md:grid-cols-2 gap-4 max-w-5xl mx-auto animate-fade-in-up"
      style="animation-delay: 0.65s"
    >
      <div
        class="glass-card hover:glass-card-hover group p-4 sm:p-5 text-left border border-green-500/16"
      >
        <div class="flex items-start justify-between gap-4 mb-3">
          <div>
            <p class="pixel-label text-green-300 mb-2">Live Now</p>
            <h2 class="text-xl sm:text-2xl font-bold text-cream">
              Vanilla SMP
            </h2>
          </div>
          <span
            class="inline-flex shrink-0 items-center gap-2 rounded-full bg-green-500/10 px-3 py-1 text-[0.7rem] uppercase tracking-wider text-green-300"
          >
            <span class="w-2 h-2 rounded-full bg-green-400 animate-pulse"
            ></span>
            Open
          </span>
        </div>
        <p class="text-cream-muted/75 leading-relaxed">
          The main world is live now with classic survival, Java and Bedrock
          cross-play, and the usual private-server chaos.
        </p>
      </div>

      <div
        class="glass-card hover:glass-card-hover group p-4 sm:p-5 text-left border border-earth-400/16"
      >
        <div class="flex items-start justify-between gap-4 mb-3">
          <div>
            <p class="pixel-label text-earth-300 mb-2">Coming Soon</p>
            <h2 class="text-xl sm:text-2xl font-bold text-cream">
              Modded Server
            </h2>
          </div>
          <span
            class="inline-flex shrink-0 items-center gap-2 rounded-full bg-earth-400/10 px-3 py-1 text-[0.7rem] uppercase tracking-wider text-earth-300"
          >
            <span class="w-2 h-2 rounded-full bg-earth-300"></span>
            In Progress
          </span>
        </div>
        <p class="text-cream-muted/75 leading-relaxed">
          The modded world is still being finalized, and will only work on Java
          Edition.
        </p>
      </div>
    </div>

    <div class="mt-8 animate-float">
      <svg
        class="w-5 h-5 mx-auto text-cream-muted/30"
        fill="none"
        viewBox="0 0 24 24"
        stroke="currentColor"
        stroke-width="1.5"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M19.5 8.25l-7.5 7.5-7.5-7.5"
        />
      </svg>
    </div>
  </div>
</section>

<ServerStatus />

<div class="max-w-7xl mx-auto px-4 sm:px-6">
  <div
    class="h-px bg-gradient-to-r from-transparent via-green-700/30 to-transparent"
  ></div>
</div>

<!-- ======================== SERVER LINEUP ======================== -->
<section id="servers" class="section-padding max-w-7xl mx-auto">
  <div class="mb-10">
    <div class="pixel-label text-green-300 mb-3 flex items-center gap-2">
      <span class="inline-block w-2 h-2 bg-green-300 rotate-45"></span>
      Server Lineup
    </div>
    <h2
      class="text-3xl sm:text-5xl font-extrabold leading-tight mb-4
             bg-gradient-to-br from-cream to-green-200 bg-clip-text text-transparent"
    >
      Two Servers, Different Modes
    </h2>
    <p class="text-lg text-cream-muted/80 max-w-3xl">
      LEKKERBOYS is built around two experiences: the live cross-platform SMP
      you can join right now, and a modded server that is still being prepared.
    </p>
  </div>

  <div class="grid grid-cols-1 lg:grid-cols-2 gap-4 sm:gap-6">
    <div class="glass-card p-5 sm:p-8 relative overflow-hidden">
      <div
        class="absolute top-0 right-0 w-40 h-40 bg-gradient-to-bl from-green-500/8 to-transparent rounded-bl-full"
      ></div>
      <div class="relative">
        <div class="flex items-start justify-between gap-4 mb-6">
          <div>
            <div
              class="pixel-label text-green-300 mb-3 flex items-center gap-2"
            >
              <span class="inline-block w-2 h-2 bg-green-300 rotate-45"></span>
              Vanilla
            </div>
            <h3 class="text-2xl sm:text-3xl font-bold text-cream mb-3">
              Main SMP
            </h3>
          </div>
          <span
            class="rounded-full border border-green-500/30 bg-green-500/10 px-3 py-1 text-[0.7rem] font-medium uppercase tracking-wider text-green-300"
          >
            Live Now
          </span>
        </div>

        <p class="text-cream-muted/75 leading-relaxed mb-6">
          This is the current server. It is the shared home world for the crew,
          with classic survival, cross-play support, and the map already
          running.
        </p>

        <div class="grid grid-cols-1 sm:grid-cols-2 gap-3 mb-6">
          <div
            class="rounded-xl border border-green-700/20 bg-surface-primary/40 p-4"
          >
            <p
              class="text-xs uppercase tracking-wider text-cream-muted/45 mb-1"
            >
              Address
            </p>
            <p class="font-mono text-green-300 text-sm">{serverAddress}</p>
          </div>
          <div
            class="rounded-xl border border-green-700/20 bg-surface-primary/40 p-4"
          >
            <p
              class="text-xs uppercase tracking-wider text-cream-muted/45 mb-1"
            >
              Port
            </p>
            <p class="text-sm text-cream-muted">25565</p>
          </div>
        </div>

        <div class="flex flex-col sm:flex-row gap-3">
          <a
            href="#connect"
            class="inline-flex w-full sm:w-auto items-center justify-center gap-2 rounded-xl bg-green-400 px-5 py-3 text-sm font-semibold text-surface-primary transition-colors hover:bg-green-300"
          >
            Join Server
          </a>
          <a
            href="#status"
            class="inline-flex w-full sm:w-auto items-center justify-center gap-2 rounded-xl border border-cream/10 bg-cream/5 px-5 py-3 text-sm font-medium text-cream transition-colors hover:bg-cream/10"
          >
            Check Status
          </a>
        </div>
      </div>
    </div>

    <div class="glass-card p-5 sm:p-8 relative overflow-hidden">
      <div
        class="absolute bottom-0 left-0 w-40 h-40 bg-gradient-to-tr from-earth-400/8 to-transparent rounded-tr-full"
      ></div>
      <div class="relative">
        <div class="flex items-start justify-between gap-4 mb-6">
          <div>
            <div
              class="pixel-label text-earth-300 mb-3 flex items-center gap-2"
            >
              <span class="inline-block w-2 h-2 bg-earth-300 rotate-45"></span>
              Modded
            </div>
            <h3 class="text-2xl sm:text-3xl font-bold text-cream mb-3">
              Next Server
            </h3>
          </div>
          <span
            class="rounded-full border border-earth-400/30 bg-earth-400/10 px-3 py-1 text-[0.7rem] font-medium uppercase tracking-wider text-earth-300"
          >
            Coming Soon
          </span>
        </div>

        <p class="text-cream-muted/75 leading-relaxed mb-6">
          The second server will be its own modded world. It is not open yet,
          and we are keeping it off the list until the setup is stable and ready
          for people to actually play.
        </p>

        <div class="space-y-3 mb-6">
          <div
            class="rounded-xl border border-earth-400/20 bg-surface-primary/40 p-4"
          >
            <p
              class="text-xs uppercase tracking-wider text-cream-muted/45 mb-1"
            >
              Status
            </p>
            <p class="text-sm text-cream-muted">In development</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="max-w-7xl mx-auto px-4 sm:px-6">
  <div
    class="h-px bg-gradient-to-r from-transparent via-green-700/30 to-transparent"
  ></div>
</div>

<HowToConnect />

<div class="max-w-7xl mx-auto px-4 sm:px-6">
  <div
    class="h-px bg-gradient-to-r from-transparent via-green-700/30 to-transparent"
  ></div>
</div>

<DynmapSection />

<script lang="ts">
    import ServerStatus from "$lib/components/ServerStatus.svelte";
    import HowToConnect from "$lib/components/HowToConnect.svelte";
    import DynmapSection from "$lib/components/DynmapSection.svelte";
    import Gallery from "$lib/components/Gallery.svelte";

    let copiedIp = $state(false);

    async function copyIp() {
        try {
            await navigator.clipboard.writeText("mc.lekkerboys.co.za");
            copiedIp = true;
            setTimeout(() => (copiedIp = false), 2500);
        } catch {
            // silently fail
        }
    }
</script>

<svelte:head>
    <title>LEKKER — Private Minecraft SMP</title>
    <meta
        name="description"
        content="LEKKER is a private whitelisted Minecraft SMP server. Java & Bedrock cross-play via Geyser."
    />
</svelte:head>

<!-- ======================== HERO SECTION ======================== -->
<section
    id="home"
    class="relative min-h-screen flex items-center justify-center overflow-hidden"
>
    <!-- Background image with parallax-like overlay -->
    <div class="absolute inset-0">
        <img
            src="/images/hero-bg.png"
            alt="LEKKER Minecraft Landscape"
            class="w-full h-full object-cover object-center"
        />
        <!-- Multi-layer gradient overlay for depth -->
        <div
            class="absolute inset-0 bg-gradient-to-b from-surface-primary/60 via-surface-primary/30 to-surface-primary"
        ></div>
        <div
            class="absolute inset-0 bg-gradient-to-r from-surface-primary/50 via-transparent to-surface-primary/50"
        ></div>
        <!-- Subtle noise texture -->
        <div
            class="absolute inset-0 opacity-[0.03]"
            style="background-image: url('data:image/svg+xml,%3Csvg viewBox=%220 0 256 256%22 xmlns=%22http://www.w3.org/2000/svg%22%3E%3Cfilter id=%22n%22%3E%3CfeTurbulence type=%22fractalNoise%22 baseFrequency=%220.9%22 numOctaves=%224%22 stitchTiles=%22stitch%22/%3E%3C/filter%3E%3Crect width=%22100%25%22 height=%22100%25%22 filter=%22url(%23n)%22/%3E%3C/svg%3E');"
        ></div>
    </div>

    <!-- Hero content -->
    <div class="relative z-10 text-center px-6 max-w-4xl mx-auto">
        <!-- Pixel label -->
        <div class="mb-6 animate-fade-in-up" style="animation-delay: 0.1s">
            <span
                class="inline-flex items-center gap-2 px-4 py-2 rounded-full
                   bg-green-500/10 border border-green-500/20 text-green-300
                   text-xs font-medium tracking-wider uppercase"
            >
                <span class="w-2 h-2 rounded-full bg-green-400 animate-pulse"
                ></span>
                Private SMP
            </span>
        </div>

        <!-- Main title -->
        <h1 class="animate-fade-in-up" style="animation-delay: 0.2s">
            <span
                class="block font-pixel text-5xl sm:text-6xl md:text-7xl lg:text-8xl text-cream
                   drop-shadow-[0_4px_0_rgba(0,0,0,0.8)] tracking-wider mb-4"
                style="text-shadow: 0 0 40px rgba(92, 180, 60, 0.2), 0 4px 0 rgba(0,0,0,0.6), 0 8px 20px rgba(0,0,0,0.4);"
            >
                LEKKER
            </span>
        </h1>

        <!-- Subtitle -->
        <p
            class="text-lg sm:text-xl text-cream-muted/80 max-w-2xl mx-auto mb-10 leading-relaxed
              animate-fade-in-up"
            style="animation-delay: 0.35s"
        >
            A private Minecraft survival server for the boys.
            <span class="text-cream">Java & Bedrock</span> cross-play,
            <span class="text-cream">vanilla vibes</span>, one world.
        </p>

        <!-- Action buttons -->
        <div
            class="flex flex-col sm:flex-row items-center justify-center gap-4
                animate-fade-in-up"
            style="animation-delay: 0.5s"
        >
            <!-- Copy IP button -->
            <button
                onclick={copyIp}
                class="group flex items-center gap-3 px-8 py-4 rounded-xl
               bg-green-500 hover:bg-green-400 text-surface-primary
               font-bold text-base transition-all duration-300
               shadow-[0_0_20px_rgba(92,180,60,0.3)] hover:shadow-[0_0_30px_rgba(92,180,60,0.5)]
               hover:scale-[1.02] active:scale-[0.98]"
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
                    <span>Copied to Clipboard!</span>
                {:else}
                    <svg
                        class="w-5 h-5 group-hover:rotate-6 transition-transform"
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
                    <span>mc.lekkerboys.co.za</span>
                    <span class="text-surface-primary/60 text-sm font-normal"
                        >— click to copy</span
                    >
                {/if}
            </button>

            <!-- Dynmap button -->
            <a
                href="#dynmap"
                class="flex items-center gap-2 px-6 py-4 rounded-xl
               bg-cream/5 hover:bg-cream/10 text-cream border border-cream/10
               hover:border-cream/25 font-medium text-base transition-all duration-300
               hover:scale-[1.02] active:scale-[0.98] backdrop-blur-sm"
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
                        d="M9 6.75V15m6-6v8.25m.503 3.498l4.875-2.437c.381-.19.622-.58.622-1.006V4.82c0-.836-.88-1.38-1.628-1.006l-3.869 1.934c-.317.159-.69.159-1.006 0L9.503 3.252a1.125 1.125 0 00-1.006 0L3.622 5.689C3.24 5.88 3 6.27 3 6.695V19.18c0 .836.88 1.38 1.628 1.006l3.869-1.934c.317-.159.69-.159 1.006 0l4.994 2.497c.317.158.69.158 1.006 0z"
                    />
                </svg>
                View Dynmap
            </a>
        </div>

        <!-- Scroll indicator -->
        <div class="mt-16 animate-float">
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

<!-- Sections -->
<ServerStatus />

<!-- Divider -->
<div class="max-w-7xl mx-auto px-6">
    <div
        class="h-px bg-gradient-to-r from-transparent via-green-700/30 to-transparent"
    ></div>
</div>

<HowToConnect />

<div class="max-w-7xl mx-auto px-6">
    <div
        class="h-px bg-gradient-to-r from-transparent via-green-700/30 to-transparent"
    ></div>
</div>

<DynmapSection />

<div class="max-w-7xl mx-auto px-6">
    <div
        class="h-px bg-gradient-to-r from-transparent via-green-700/30 to-transparent"
    ></div>
</div>

<Gallery />

<div class="max-w-7xl mx-auto px-6">
    <div
        class="h-px bg-gradient-to-r from-transparent via-green-700/30 to-transparent"
    ></div>
</div>

<!-- ======================== COMING SOON — MODDED SERVER ======================== -->
<section class="section-padding max-w-7xl mx-auto">
    <div class="glass-card p-8 sm:p-12 relative overflow-hidden">
        <!-- Background decoration -->
        <div
            class="absolute top-0 right-0 w-64 h-64 bg-gradient-to-bl from-green-500/5 to-transparent rounded-bl-full"
        ></div>
        <div
            class="absolute bottom-0 left-0 w-48 h-48 bg-gradient-to-tr from-sky-500/5 to-transparent rounded-tr-full"
        ></div>

        <div class="relative flex flex-col md:flex-row items-center gap-8">
            <!-- Icon -->
            <div
                class="w-20 h-20 rounded-2xl bg-gradient-to-br from-green-600/30 to-sky-600/20
                  flex items-center justify-center border border-green-600/20
                  animate-float shrink-0"
            >
                <svg
                    class="w-10 h-10 text-green-300"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                    stroke-width="1.5"
                >
                    <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        d="M9.813 15.904L9 18.75l-.813-2.846a4.5 4.5 0 00-3.09-3.09L2.25 12l2.846-.813a4.5 4.5 0 003.09-3.09L9 5.25l.813 2.846a4.5 4.5 0 003.09 3.09L15.75 12l-2.846.813a4.5 4.5 0 00-3.09 3.09zM18.259 8.715L18 9.75l-.259-1.035a3.375 3.375 0 00-2.455-2.456L14.25 6l1.036-.259a3.375 3.375 0 002.455-2.456L18 2.25l.259 1.035a3.375 3.375 0 002.455 2.456L21.75 6l-1.036.259a3.375 3.375 0 00-2.455 2.456zM16.894 20.567L16.5 21.75l-.394-1.183a2.25 2.25 0 00-1.423-1.423L13.5 18.75l1.183-.394a2.25 2.25 0 001.423-1.423l.394-1.183.394 1.183a2.25 2.25 0 001.423 1.423l1.183.394-1.183.394a2.25 2.25 0 00-1.423 1.423z"
                    />
                </svg>
            </div>

            <div class="text-center md:text-left">
                <div
                    class="pixel-label text-earth-300 mb-3 flex items-center gap-2 justify-center md:justify-start"
                >
                    <span class="inline-block w-2 h-2 bg-earth-300 rotate-45"
                    ></span>
                    Coming Soon
                </div>
                <h3 class="text-2xl sm:text-3xl font-bold text-cream mb-3">
                    Modded Server
                </h3>
                <p class="text-cream-muted/70 max-w-lg leading-relaxed">
                    We're considering opening a modded server alongside the
                    vanilla SMP. Stay tuned for updates — it's going to be <span
                        class="text-green-300 font-semibold">lekker</span
                    >.
                </p>
            </div>
        </div>
    </div>
</section>

<!-- ======================== DISCORD SECTION ======================== -->
<section class="section-padding max-w-7xl mx-auto">
    <div class="flex flex-col items-center text-center">
        <div
            class="w-16 h-16 rounded-2xl bg-[#5865F2]/20 flex items-center justify-center mb-6
                border border-[#5865F2]/20"
        >
            <svg
                class="w-8 h-8 text-[#5865F2]"
                viewBox="0 0 24 24"
                fill="currentColor"
            >
                <path
                    d="M20.317 4.37a19.791 19.791 0 0 0-4.885-1.515.074.074 0 0 0-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 0 0-5.487 0 12.64 12.64 0 0 0-.617-1.25.077.077 0 0 0-.079-.037A19.736 19.736 0 0 0 3.677 4.37a.07.07 0 0 0-.032.027C.533 9.046-.32 13.58.099 18.057a.082.082 0 0 0 .031.057 19.9 19.9 0 0 0 5.993 3.03.078.078 0 0 0 .084-.028 14.09 14.09 0 0 0 1.226-1.994.076.076 0 0 0-.041-.106 13.107 13.107 0 0 1-1.872-.892.077.077 0 0 1-.008-.128 10.2 10.2 0 0 0 .372-.292.074.074 0 0 1 .077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 0 1 .078.01c.12.098.246.198.373.292a.077.077 0 0 1-.006.127 12.299 12.299 0 0 1-1.873.892.077.077 0 0 0-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 0 0 .084.028 19.839 19.839 0 0 0 6.002-3.03.077.077 0 0 0 .032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 0 0-.031-.03zM8.02 15.33c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.956-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.956 2.418-2.157 2.418zm7.975 0c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.956-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.946 2.418-2.157 2.418z"
                />
            </svg>
        </div>
        <h3 class="text-2xl font-bold text-cream mb-3">Join the Discord</h3>
        <p class="text-cream-muted/70 max-w-md mb-8 leading-relaxed">
            Chat with the crew, share screenshots, and stay up to date with
            server announcements.
        </p>
        <a
            href="https://discord.gg/your-invite"
            target="_blank"
            rel="noopener noreferrer"
            class="flex items-center gap-3 px-8 py-4 rounded-xl
             bg-[#5865F2] hover:bg-[#4752C4] text-white
             font-semibold text-base transition-all duration-300
             shadow-[0_0_20px_rgba(88,101,242,0.3)] hover:shadow-[0_0_30px_rgba(88,101,242,0.5)]
             hover:scale-[1.02] active:scale-[0.98]"
        >
            <svg class="w-5 h-5" viewBox="0 0 24 24" fill="currentColor">
                <path
                    d="M20.317 4.37a19.791 19.791 0 0 0-4.885-1.515.074.074 0 0 0-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 0 0-5.487 0 12.64 12.64 0 0 0-.617-1.25.077.077 0 0 0-.079-.037A19.736 19.736 0 0 0 3.677 4.37a.07.07 0 0 0-.032.027C.533 9.046-.32 13.58.099 18.057a.082.082 0 0 0 .031.057 19.9 19.9 0 0 0 5.993 3.03.078.078 0 0 0 .084-.028 14.09 14.09 0 0 0 1.226-1.994.076.076 0 0 0-.041-.106 13.107 13.107 0 0 1-1.872-.892.077.077 0 0 1-.008-.128 10.2 10.2 0 0 0 .372-.292.074.074 0 0 1 .077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 0 1 .078.01c.12.098.246.198.373.292a.077.077 0 0 1-.006.127 12.299 12.299 0 0 1-1.873.892.077.077 0 0 0-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 0 0 .084.028 19.839 19.839 0 0 0 6.002-3.03.077.077 0 0 0 .032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 0 0-.031-.03zM8.02 15.33c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.956-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.956 2.418-2.157 2.418zm7.975 0c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.956-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.946 2.418-2.157 2.418z"
                />
            </svg>
            Join Our Server
        </a>
    </div>
</section>

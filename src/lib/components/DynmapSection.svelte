<section id="dynmap" class="section-padding max-w-7xl mx-auto">
  <div class="mb-8 sm:mb-10">
    <div class="pixel-label text-green-300 mb-3 flex items-center gap-2">
      <span class="inline-block w-2 h-2 bg-green-300 rotate-45"></span>
      Vanilla World Map
    </div>
    <h2
      class="text-3xl sm:text-5xl font-extrabold leading-tight mb-4
               bg-gradient-to-br from-cream to-green-200 bg-clip-text text-transparent"
    >
      Vanilla Dynmap
    </h2>
    <p class="text-lg text-cream-muted/80 max-w-xl">
      Explore the live vanilla world in real-time. See builds, terrain, and
      player positions on the map.
    </p>
  </div>

  <!-- Dynmap embed container -->
  <div
    class="glass-card p-2 sm:p-3 overflow-hidden hover:glass-card-hover group"
  >
    <div class="relative rounded-xl overflow-hidden bg-surface-primary">
      <!-- Map iframe -->
      <div class="aspect-video w-full relative">
        <iframe
          src="http://mc.lekkerboys.co.za:8123"
          title="LEKKERBOYS Vanilla Dynmap - Live World Map"
          class="w-full h-full border-0 rounded-xl"
          loading="lazy"
          sandbox="allow-scripts allow-same-origin"
        ></iframe>

        <!-- Overlay gradient at bottom -->
        <div
          class="absolute bottom-0 left-0 right-0 h-20 bg-gradient-to-t from-surface-primary/80 to-transparent
                    pointer-events-none"
        ></div>
      </div>

      <!-- Map controls bar -->
      <div
        class="absolute bottom-0 left-0 right-0 p-3 sm:p-4 flex flex-col sm:flex-row items-start sm:items-center justify-between gap-3 z-10"
      >
        <div class="flex items-center gap-2">
          <div class="w-2 h-2 rounded-full bg-green-400 animate-pulse"></div>
          <span class="text-xs text-cream-muted/80">Live</span>
        </div>
        <a
          href="http://map.lekkerboys.co.za"
          target="_blank"
          rel="noopener noreferrer"
          class="flex w-full sm:w-auto items-center justify-center gap-2 px-4 py-2 bg-green-600/40 hover:bg-green-500/50
                 text-green-200 text-sm font-medium rounded-lg transition-all duration-200
                 border border-green-600/30 hover:border-green-400/50
                 backdrop-blur-sm"
        >
          <svg
            class="w-4 h-4"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            stroke-width="2"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M13.5 6H5.25A2.25 2.25 0 003 8.25v10.5A2.25 2.25 0 005.25 21h10.5A2.25 2.25 0 0018 18.75V10.5m-10.5 6L21 3m0 0h-5.25M21 3v5.25"
            />
          </svg>
          Open Full Map
        </a>
      </div>
    </div>
  </div>
</section>

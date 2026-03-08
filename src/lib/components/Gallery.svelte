<section id="gallery" class="section-padding max-w-7xl mx-auto">
    <div class="mb-10">
        <div class="pixel-label text-green-300 mb-3 flex items-center gap-2">
            <span class="inline-block w-2 h-2 bg-green-300 rotate-45"></span>
            Gallery
        </div>
        <h2
            class="text-4xl sm:text-5xl font-extrabold leading-tight mb-4
               bg-gradient-to-br from-cream to-green-200 bg-clip-text text-transparent"
        >
            Our Builds
        </h2>
        <p class="text-lg text-cream-muted/80 max-w-xl">
            Screenshots and builds from the LEKKER SMP. The best of our blocky
            adventures.
        </p>
    </div>

    <!-- Gallery grid - placeholder for now -->
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4">
        {#each Array(6) as _, i}
            <div
                class="glass-card p-0 overflow-hidden group hover:glass-card-hover
                  {i === 0 ? 'sm:col-span-2 sm:row-span-2' : ''}"
            >
                <div
                    class="aspect-video {i === 0
                        ? 'sm:aspect-square'
                        : ''} w-full
                    bg-gradient-to-br from-green-900/40 to-surface-primary
                    flex flex-col items-center justify-center gap-4 relative overflow-hidden"
                >
                    <!-- Decorative grid pattern -->
                    <div
                        class="absolute inset-0 opacity-5"
                        style="background-image: repeating-linear-gradient(0deg, transparent, transparent 31px, rgba(92,180,60,0.3) 31px, rgba(92,180,60,0.3) 32px),
                      repeating-linear-gradient(90deg, transparent, transparent 31px, rgba(92,180,60,0.3) 31px, rgba(92,180,60,0.3) 32px);"
                    ></div>

                    <div class="relative z-10 flex flex-col items-center gap-3">
                        <svg
                            class="w-10 h-10 text-green-700/60 group-hover:text-green-600/80 transition-colors"
                            fill="none"
                            viewBox="0 0 24 24"
                            stroke="currentColor"
                            stroke-width="1"
                        >
                            <path
                                stroke-linecap="round"
                                stroke-linejoin="round"
                                d="M2.25 15.75l5.159-5.159a2.25 2.25 0 013.182 0l5.159 5.159m-1.5-1.5l1.409-1.409a2.25 2.25 0 013.182 0l2.909 2.909M3.75 21h16.5A2.25 2.25 0 0022.5 18.75V5.25A2.25 2.25 0 0020.25 3H3.75A2.25 2.25 0 001.5 5.25v13.5A2.25 2.25 0 003.75 21z"
                            />
                        </svg>
                        <span class="text-sm text-cream-muted/40 font-medium"
                            >Coming Soon</span
                        >
                    </div>
                </div>
            </div>
        {/each}
    </div>
</section>

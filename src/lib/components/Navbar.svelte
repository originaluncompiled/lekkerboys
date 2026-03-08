<script lang="ts">
  let mobileOpen = $state(false);

  function toggleMobile() {
    mobileOpen = !mobileOpen;
  }

  function closeMobile() {
    mobileOpen = false;
  }

  const navLinks = [
    { label: 'Home', href: '#home' },
    { label: 'Servers', href: '#servers' },
    { label: 'Connect', href: '#connect' },
    { label: 'Status', href: '#status' },
    { label: 'Dynmap', href: '#dynmap' },
  ];
</script>

<nav class="fixed top-0 left-0 right-0 z-50 transition-all duration-300">
  <!-- Glassmorphism background -->
  <div class="absolute inset-0 bg-surface-secondary/70 backdrop-blur-xl border-b border-white/8"></div>
  
  <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <div class="flex items-center justify-between h-16">
      <!-- Logo -->
      <a href="#home" class="flex items-center gap-3 group" onclick={closeMobile}>
        <img
          src="/images/lekkerlogo.png"
          alt="LEKKERBOYS logo"
          class="w-9 h-9 rounded-lg object-contain drop-shadow-[0_0_12px_rgba(92,180,60,0.3)] group-hover:drop-shadow-[0_0_20px_rgba(92,180,60,0.5)] transition-all duration-300"
        />
        <span class="font-pixel text-[0.8rem] sm:text-[0.68rem] md:text-[0.74rem] lg:text-[0.8rem] text-cream tracking-wider">LEKKERBOYS</span>
      </a>

      <!-- Desktop Nav -->
      <div class="hidden md:flex items-center gap-1">
        {#each navLinks as link}
          <a
            href={link.href}
            class="px-3 py-2 text-sm text-cream-muted hover:text-cream transition-all duration-200
                   rounded-lg border border-transparent hover:border-white/10 hover:bg-white/8 hover:backdrop-blur-sm"
          >
            {link.label}
          </a>
        {/each}
      </div>

      <!-- Right side buttons -->
      <div class="flex items-center gap-3">
        <!-- Login/Panel button -->
        <a
          href="https://panel.lekkerboys.co.za"
          target="_blank"
          rel="noopener noreferrer"
          class="hidden sm:flex items-center gap-2 px-4 py-2 text-sm font-semibold
                 bg-green-400 hover:bg-green-300 text-surface-primary 
                 rounded-lg border border-white/10 transition-all duration-200 backdrop-blur-sm
                 shadow-[0_0_12px_rgba(92,180,60,0.18)] hover:shadow-[0_0_20px_rgba(92,180,60,0.28)] hover:border-white/20"
        >
          <svg class="w-4 h-4" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 9V5.25A2.25 2.25 0 0013.5 3h-6a2.25 2.25 0 00-2.25 2.25v13.5A2.25 2.25 0 007.5 21h6a2.25 2.25 0 002.25-2.25V15m3 0l3-3m0 0l-3-3m3 3H9" />
          </svg>
          Panel
        </a>

        <!-- Mobile hamburger -->
        <button
          class="md:hidden flex flex-col gap-1.5 p-2"
          onclick={toggleMobile}
          aria-label="Toggle navigation"
        >
          <span class="block w-5 h-0.5 bg-cream transition-all duration-300
                       {mobileOpen ? 'rotate-45 translate-y-2' : ''}"></span>
          <span class="block w-5 h-0.5 bg-cream transition-all duration-300
                       {mobileOpen ? 'opacity-0' : ''}"></span>
          <span class="block w-5 h-0.5 bg-cream transition-all duration-300
                       {mobileOpen ? '-rotate-45 -translate-y-2' : ''}"></span>
        </button>
      </div>
    </div>
  </div>

  <!-- Mobile menu -->
  {#if mobileOpen}
    <div class="md:hidden absolute top-16 left-0 right-0 bg-surface-secondary/88 backdrop-blur-xl
                border-b border-white/8 animate-fade-in-up">
      <div class="px-4 py-4 flex flex-col gap-1">
        {#each navLinks as link}
          <a
            href={link.href}
            class="px-4 py-3 text-sm text-cream-muted hover:text-cream hover:bg-white/8
                   rounded-lg border border-transparent hover:border-white/10 transition-all duration-200"
            onclick={closeMobile}
          >
            {link.label}
          </a>
        {/each}
        <a
          href="https://panel.lekkerboys.co.za"
          target="_blank"
          rel="noopener noreferrer"
          class="mt-2 flex items-center justify-center gap-2 rounded-lg bg-green-400 px-4 py-3 text-sm font-semibold text-surface-primary border border-white/10 transition-all duration-200 backdrop-blur-sm hover:bg-green-300 hover:border-white/20"
          onclick={closeMobile}
        >
          Panel
        </a>
      </div>
    </div>
  {/if}
</nav>

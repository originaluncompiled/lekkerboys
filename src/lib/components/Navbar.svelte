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
    { label: 'Status', href: '#status' },
    { label: 'Connect', href: '#connect' },
    { label: 'Dynmap', href: '#dynmap' },
    { label: 'Gallery', href: '#gallery' }
  ];
</script>

<nav class="fixed top-0 left-0 right-0 z-50 transition-all duration-300">
  <!-- Glassmorphism background -->
  <div class="absolute inset-0 bg-surface-primary/80 backdrop-blur-xl border-b border-green-700/20"></div>
  
  <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <div class="flex items-center justify-between h-16">
      <!-- Logo -->
      <a href="#home" class="flex items-center gap-3 group" onclick={closeMobile}>
        <div class="w-8 h-8 bg-green-400 rounded-sm flex items-center justify-center
                    shadow-[0_0_12px_rgba(92,180,60,0.3)] group-hover:shadow-[0_0_20px_rgba(92,180,60,0.5)]
                    transition-shadow duration-300">
          <span class="text-surface-primary font-black text-sm">L</span>
        </div>
        <span class="font-pixel text-[0.7rem] text-cream tracking-wider hidden sm:block">LEKKER</span>
      </a>

      <!-- Desktop Nav -->
      <div class="hidden md:flex items-center gap-1">
        {#each navLinks as link}
          <a
            href={link.href}
            class="px-3 py-2 text-sm text-cream-muted hover:text-cream transition-colors duration-200
                   rounded-lg hover:bg-green-800/30"
          >
            {link.label}
          </a>
        {/each}
      </div>

      <!-- Right side buttons -->
      <div class="flex items-center gap-3">
        <!-- Discord -->
        <a
          href="https://discord.gg/your-invite"
          target="_blank"
          rel="noopener noreferrer"
          class="hidden sm:flex items-center gap-2 px-3 py-1.5 text-sm text-cream-muted 
                 hover:text-cream rounded-lg hover:bg-green-800/30 transition-all duration-200"
          aria-label="Discord"
        >
          <svg class="w-4 h-4" viewBox="0 0 24 24" fill="currentColor">
            <path d="M20.317 4.37a19.791 19.791 0 0 0-4.885-1.515.074.074 0 0 0-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 0 0-5.487 0 12.64 12.64 0 0 0-.617-1.25.077.077 0 0 0-.079-.037A19.736 19.736 0 0 0 3.677 4.37a.07.07 0 0 0-.032.027C.533 9.046-.32 13.58.099 18.057a.082.082 0 0 0 .031.057 19.9 19.9 0 0 0 5.993 3.03.078.078 0 0 0 .084-.028 14.09 14.09 0 0 0 1.226-1.994.076.076 0 0 0-.041-.106 13.107 13.107 0 0 1-1.872-.892.077.077 0 0 1-.008-.128 10.2 10.2 0 0 0 .372-.292.074.074 0 0 1 .077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 0 1 .078.01c.12.098.246.198.373.292a.077.077 0 0 1-.006.127 12.299 12.299 0 0 1-1.873.892.077.077 0 0 0-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 0 0 .084.028 19.839 19.839 0 0 0 6.002-3.03.077.077 0 0 0 .032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 0 0-.031-.03zM8.02 15.33c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.956-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.956 2.418-2.157 2.418zm7.975 0c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.956-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.946 2.418-2.157 2.418z"/>
          </svg>
          <span class="text-xs">Discord</span>
        </a>

        <!-- Login/Panel button -->
        <a
          href="https://panel.lekkerboys.co.za"
          target="_blank"
          rel="noopener noreferrer"
          class="flex items-center gap-2 px-4 py-2 text-sm font-semibold
                 bg-green-500 hover:bg-green-400 text-surface-primary 
                 rounded-lg transition-all duration-200
                 shadow-[0_0_12px_rgba(92,180,60,0.3)] hover:shadow-[0_0_20px_rgba(92,180,60,0.5)]"
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
    <div class="md:hidden absolute top-16 left-0 right-0 bg-surface-primary/95 backdrop-blur-xl
                border-b border-green-700/20 animate-fade-in-up">
      <div class="px-4 py-4 flex flex-col gap-1">
        {#each navLinks as link}
          <a
            href={link.href}
            class="px-4 py-3 text-sm text-cream-muted hover:text-cream hover:bg-green-800/30
                   rounded-lg transition-colors duration-200"
            onclick={closeMobile}
          >
            {link.label}
          </a>
        {/each}
        <a
          href="https://discord.gg/your-invite"
          target="_blank"
          rel="noopener noreferrer"
          class="px-4 py-3 text-sm text-cream-muted hover:text-cream hover:bg-green-800/30
                 rounded-lg transition-colors duration-200 flex items-center gap-2"
        >
          <svg class="w-4 h-4" viewBox="0 0 24 24" fill="currentColor">
            <path d="M20.317 4.37a19.791 19.791 0 0 0-4.885-1.515.074.074 0 0 0-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 0 0-5.487 0 12.64 12.64 0 0 0-.617-1.25.077.077 0 0 0-.079-.037A19.736 19.736 0 0 0 3.677 4.37a.07.07 0 0 0-.032.027C.533 9.046-.32 13.58.099 18.057a.082.082 0 0 0 .031.057 19.9 19.9 0 0 0 5.993 3.03.078.078 0 0 0 .084-.028 14.09 14.09 0 0 0 1.226-1.994.076.076 0 0 0-.041-.106 13.107 13.107 0 0 1-1.872-.892.077.077 0 0 1-.008-.128 10.2 10.2 0 0 0 .372-.292.074.074 0 0 1 .077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 0 1 .078.01c.12.098.246.198.373.292a.077.077 0 0 1-.006.127 12.299 12.299 0 0 1-1.873.892.077.077 0 0 0-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 0 0 .084.028 19.839 19.839 0 0 0 6.002-3.03.077.077 0 0 0 .032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 0 0-.031-.03zM8.02 15.33c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.956-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.956 2.418-2.157 2.418zm7.975 0c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.956-2.419 2.157-2.419 1.21 0 2.176 1.096 2.157 2.42 0 1.333-.946 2.418-2.157 2.418z"/>
          </svg>
          Discord
        </a>
      </div>
    </div>
  {/if}
</nav>

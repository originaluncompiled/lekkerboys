<script lang="ts">
    interface ServerData {
        online: boolean;
        players: {
            online: number;
            max: number;
            list?: Array<{ name: string; uuid: string }>;
        };
        version?: string;
        motd?: { clean: string[] };
        icon?: string;
    }

    let serverData = $state<ServerData | null>(null);
    let loading = $state(true);
    let error = $state(false);

    async function fetchStatus() {
        try {
            const res = await fetch(
                "https://api.mcsrvstat.us/3/mc.lekkerboys.co.za",
            );
            if (!res.ok) throw new Error("Failed to fetch");
            const data: ServerData = await res.json();
            serverData = data;
            error = false;
        } catch {
            error = true;
        } finally {
            loading = false;
        }
    }

    // Fetch on mount and every 60s
    $effect(() => {
        fetchStatus();
        const interval = setInterval(fetchStatus, 60000);
        return () => clearInterval(interval);
    });
</script>

<section id="status" class="section-padding max-w-7xl mx-auto">
    <!-- Section header -->
    <div class="mb-10">
        <div class="pixel-label text-green-300 mb-3 flex items-center gap-2">
            <span class="inline-block w-2 h-2 bg-green-300 rotate-45"></span>
            Server Status
        </div>
        <h2
            class="text-4xl sm:text-5xl font-extrabold leading-tight mb-4
               bg-gradient-to-br from-cream to-green-200 bg-clip-text text-transparent"
        >
            Live Server
        </h2>
        <p class="text-lg text-cream-muted/80 max-w-xl">
            Real-time status of the LEKKER SMP. See who's online right now.
        </p>
    </div>

    <!-- Status cards grid -->
    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
        <!-- Main status card -->
        <div class="glass-card p-8 md:col-span-2 hover:glass-card-hover group">
            {#if loading}
                <div class="flex items-center gap-3">
                    <div
                        class="w-4 h-4 rounded-full bg-green-500/30 animate-pulse"
                    ></div>
                    <span class="text-cream-muted text-sm"
                        >Checking server status...</span
                    >
                </div>
            {:else if error}
                <div class="flex items-center gap-3">
                    <div class="w-4 h-4 rounded-full bg-red-500/80"></div>
                    <span class="text-cream-muted">Could not reach server</span>
                </div>
            {:else if serverData}
                <div class="flex flex-col gap-6">
                    <!-- Online indicator + player count -->
                    <div
                        class="flex items-start justify-between flex-wrap gap-4"
                    >
                        <div class="flex items-center gap-4">
                            <div class="relative">
                                <div
                                    class="w-5 h-5 rounded-full {serverData.online
                                        ? 'bg-green-400'
                                        : 'bg-red-500'}
                            {serverData.online ? 'animate-pulse-glow' : ''}"
                                ></div>
                                {#if serverData.online}
                                    <div
                                        class="absolute inset-0 w-5 h-5 rounded-full bg-green-400/30 animate-ping"
                                    ></div>
                                {/if}
                            </div>
                            <div>
                                <span class="text-2xl font-bold text-cream">
                                    {serverData.online ? "Online" : "Offline"}
                                </span>
                                {#if serverData.version}
                                    <p
                                        class="text-sm text-cream-muted/60 mt-0.5"
                                    >
                                        Minecraft {serverData.version}
                                    </p>
                                {/if}
                            </div>
                        </div>

                        {#if serverData.online}
                            <div class="flex flex-col items-end">
                                <div class="text-4xl font-black text-green-300">
                                    {serverData.players.online}
                                    <span
                                        class="text-lg text-cream-muted/50 font-normal"
                                        >/ {serverData.players.max}</span
                                    >
                                </div>
                                <span class="text-xs text-cream-muted/50 mt-1"
                                    >players online</span
                                >
                            </div>
                        {/if}
                    </div>

                    <!-- Player bar -->
                    {#if serverData.online}
                        <div
                            class="w-full h-3 bg-green-900/40 rounded-full overflow-hidden"
                        >
                            <div
                                class="h-full bg-gradient-to-r from-green-500 to-green-300 rounded-full transition-all duration-1000 ease-out"
                                style="width: {(serverData.players.online /
                                    serverData.players.max) *
                                    100}%"
                            ></div>
                        </div>
                    {/if}

                    <!-- Player list -->
                    {#if serverData.players?.list && serverData.players.list.length > 0}
                        <div>
                            <span
                                class="text-xs text-cream-muted/50 uppercase tracking-wider mb-3 block"
                                >Online Now</span
                            >
                            <div class="flex flex-wrap gap-2">
                                {#each serverData.players.list as player}
                                    <div
                                        class="flex items-center gap-2 px-3 py-1.5 bg-green-900/30 rounded-lg
                              border border-green-700/20 hover:border-green-600/40 transition-colors"
                                    >
                                        <img
                                            src="https://mc-heads.net/avatar/{player.uuid}/24"
                                            alt={player.name}
                                            class="w-6 h-6 rounded-sm image-rendering-pixelated"
                                        />
                                        <span class="text-sm text-cream"
                                            >{player.name}</span
                                        >
                                    </div>
                                {/each}
                            </div>
                        </div>
                    {/if}
                </div>
            {/if}
        </div>

        <!-- Quick stats column -->
        <div class="flex flex-col gap-6">
            <!-- Server type card -->
            <div class="glass-card p-6 hover:glass-card-hover">
                <div class="flex items-center gap-3 mb-3">
                    <div
                        class="w-10 h-10 rounded-lg bg-green-800/40 flex items-center justify-center"
                    >
                        <svg
                            class="w-5 h-5 text-green-300"
                            fill="none"
                            viewBox="0 0 24 24"
                            stroke="currentColor"
                            stroke-width="1.5"
                        >
                            <path
                                stroke-linecap="round"
                                stroke-linejoin="round"
                                d="M5.25 14.25h13.5m-13.5 0a3 3 0 01-3-3m3 3a3 3 0 100 6h13.5a3 3 0 100-6m-16.5-3a3 3 0 013-3h13.5a3 3 0 013 3m-19.5 0a4.5 4.5 0 01.9-2.7L5.737 5.1a3.375 3.375 0 012.7-1.35h7.126c1.062 0 2.062.5 2.7 1.35l2.587 3.45a4.5 4.5 0 01.9 2.7m0 0a3 3 0 01-3 3m0 3h.008v.008h-.008v-.008zm0-6h.008v.008h-.008v-.008zm-3 6h.008v.008h-.008v-.008zm0-6h.008v.008h-.008v-.008z"
                            />
                        </svg>
                    </div>
                    <div>
                        <p
                            class="text-xs text-cream-muted/60 uppercase tracking-wider"
                        >
                            Server Type
                        </p>
                        <p class="text-cream font-semibold">Paper SMP</p>
                    </div>
                </div>
                <p class="text-xs text-cream-muted/50">
                    Vanilla survival with Geyser for cross-play
                </p>
            </div>

            <!-- Edition support card -->
            <div class="glass-card p-6 hover:glass-card-hover">
                <div class="flex items-center gap-3 mb-3">
                    <div
                        class="w-10 h-10 rounded-lg bg-sky-400/20 flex items-center justify-center"
                    >
                        <svg
                            class="w-5 h-5 text-sky-300"
                            fill="none"
                            viewBox="0 0 24 24"
                            stroke="currentColor"
                            stroke-width="1.5"
                        >
                            <path
                                stroke-linecap="round"
                                stroke-linejoin="round"
                                d="M10.5 1.5H8.25A2.25 2.25 0 006 3.75v16.5a2.25 2.25 0 002.25 2.25h7.5A2.25 2.25 0 0018 20.25V3.75a2.25 2.25 0 00-2.25-2.25H13.5m-3 0V3h3V1.5m-3 0h3m-3 18.75h3"
                            />
                        </svg>
                    </div>
                    <div>
                        <p
                            class="text-xs text-cream-muted/60 uppercase tracking-wider"
                        >
                            Platforms
                        </p>
                        <p class="text-cream font-semibold">Java + Bedrock</p>
                    </div>
                </div>
                <p class="text-xs text-cream-muted/50">
                    Play from any device via Geyser
                </p>
            </div>

            <!-- Whitelist card -->
            <div class="glass-card p-6 hover:glass-card-hover">
                <div class="flex items-center gap-3 mb-3">
                    <div
                        class="w-10 h-10 rounded-lg bg-earth-400/20 flex items-center justify-center"
                    >
                        <svg
                            class="w-5 h-5 text-earth-300"
                            fill="none"
                            viewBox="0 0 24 24"
                            stroke="currentColor"
                            stroke-width="1.5"
                        >
                            <path
                                stroke-linecap="round"
                                stroke-linejoin="round"
                                d="M16.5 10.5V6.75a4.5 4.5 0 10-9 0v3.75m-.75 11.25h10.5a2.25 2.25 0 002.25-2.25v-6.75a2.25 2.25 0 00-2.25-2.25H6.75a2.25 2.25 0 00-2.25 2.25v6.75a2.25 2.25 0 002.25 2.25z"
                            />
                        </svg>
                    </div>
                    <div>
                        <p
                            class="text-xs text-cream-muted/60 uppercase tracking-wider"
                        >
                            Access
                        </p>
                        <p class="text-cream font-semibold">Whitelisted</p>
                    </div>
                </div>
                <p class="text-xs text-cream-muted/50">
                    Private SMP for the boys
                </p>
            </div>
        </div>
    </div>
</section>

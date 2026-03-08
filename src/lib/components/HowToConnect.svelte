<script lang="ts">
    let copiedJava = $state(false);
    let copiedBedrock = $state(false);

    async function copyToClipboard(text: string, edition: "java" | "bedrock") {
        try {
            await navigator.clipboard.writeText(text);
            if (edition === "java") {
                copiedJava = true;
                setTimeout(() => (copiedJava = false), 2000);
            } else {
                copiedBedrock = true;
                setTimeout(() => (copiedBedrock = false), 2000);
            }
        } catch {
            // Fallback
            const el = document.createElement("textarea");
            el.value = text;
            document.body.appendChild(el);
            el.select();
            document.execCommand("copy");
            document.body.removeChild(el);
        }
    }
</script>

<section id="connect" class="section-padding max-w-7xl mx-auto">
    <div class="mb-8 sm:mb-10">
        <div class="pixel-label text-green-300 mb-3 flex items-center gap-2">
            <span class="inline-block w-2 h-2 bg-green-300 rotate-45"></span>
            Cross-Platform Server
        </div>
        <h2
            class="text-3xl sm:text-5xl font-extrabold leading-tight mb-4
               bg-gradient-to-br from-cream to-green-200 bg-clip-text text-transparent"
        >
            Join the Server
        </h2>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 sm:gap-6">
        <!-- Java Edition Card -->
        <div
            class="glass-card p-5 sm:p-8 hover:glass-card-hover group relative overflow-hidden"
        >
            <!-- Decorative corner -->
            <div
                class="absolute top-0 right-0 w-24 h-24 bg-gradient-to-bl from-green-500/10 to-transparent rounded-bl-3xl"
            ></div>

            <div class="relative">
                <div class="flex items-center gap-3 sm:gap-4 mb-5 sm:mb-6">
                    <div
                        class="w-12 h-12 sm:w-14 sm:h-14 rounded-xl bg-green-800/40 flex items-center justify-center
                      border border-green-700/30 group-hover:border-green-600/50 transition-colors"
                    >
                        <svg
                            class="w-6 h-6 sm:w-7 sm:h-7 text-green-300"
                            viewBox="0 0 24 24"
                            fill="currentColor"
                        >
                            <path
                                d="M8.851 18.56s-.917.534.653.714c1.902.218 2.874.187 4.969-.211 0 0 .552.346 1.321.646-4.699 2.013-10.633-.118-6.943-1.149M8.276 15.933s-1.028.762.542.924c2.032.209 3.636.227 6.413-.308 0 0 .384.389.987.602-5.679 1.661-12.007.13-7.942-1.218M13.116 11.475c1.158 1.333-.304 2.533-.304 2.533s2.939-1.518 1.589-3.418c-1.261-1.772-2.228-2.652 3.007-5.688 0-.001-8.216 2.051-4.292 6.573"
                            />
                            <path
                                d="M19.33 20.504s.679.559-.747.991c-2.712.822-11.288 1.069-13.669.033-.856-.373.75-.89 1.254-.998.527-.114.828-.093.828-.093-.953-.671-6.156 1.317-2.643 1.887 9.58 1.553 17.462-.7 14.977-1.82M9.292 13.21s-4.362 1.036-1.544 1.412c1.189.159 3.561.123 5.77-.062 1.806-.152 3.618-.477 3.618-.477s-.637.272-1.098.587c-4.429 1.165-12.986.623-10.522-.568 2.082-1.006 3.776-.892 3.776-.892M17.116 17.584c4.503-2.34 2.421-4.589.968-4.285-.356.074-.515.138-.515.138s.132-.207.385-.297c2.875-1.011 5.086 2.981-.928 4.562 0 0 .07-.062.09-.118"
                            />
                            <path
                                d="M14.401 0s2.494 2.494-2.365 6.33c-3.896 3.077-.889 4.832 0 6.836-2.274-2.053-3.943-3.858-2.824-5.539 1.644-2.469 6.197-3.665 5.189-7.627"
                            />
                            <path
                                d="M9.734 23.924c4.322.277 10.959-.154 11.116-2.198 0 0-.302.775-3.572 1.391-3.688.694-8.239.613-10.937.168 0 0 .553.457 3.393.639"
                            />
                        </svg>
                    </div>
                    <div>
                        <h3 class="text-lg sm:text-xl font-bold text-cream">
                            Java Edition
                        </h3>
                        <p class="text-sm text-cream-muted/60">
                            Desktop / PC / Mac
                        </p>
                    </div>
                </div>

                <!-- Server IP -->
                <div class="mb-6">
                    <p
                        class="text-xs text-cream-muted/50 uppercase tracking-wider mb-2 block"
                        >Server Address</p
                    >
                    <div class="flex flex-col sm:flex-row items-stretch sm:items-center gap-2">
                        <div
                            class="flex-1 bg-surface-primary/60 rounded-lg px-4 py-3 font-mono text-green-300 text-sm break-all
                        border border-green-700/20"
                        >
                            mc.lekkerboys.co.za
                        </div>
                        <button
                            onclick={() =>
                                copyToClipboard("mc.lekkerboys.co.za", "java")}
                            class="w-full sm:w-auto px-4 py-3 bg-green-500/25 hover:bg-green-400/35 rounded-lg
                     text-green-300 text-sm font-medium transition-all duration-200
                     border border-green-500/30 hover:border-green-400/50
                     flex items-center gap-2 justify-center"
                        >
                            {#if copiedJava}
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
                                        d="M4.5 12.75l6 6 9-13.5"
                                    />
                                </svg>
                                Copied!
                            {:else}
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
                                        d="M15.666 3.888A2.25 2.25 0 0013.5 2.25h-3c-1.03 0-1.9.693-2.166 1.638m7.332 0c.055.194.084.4.084.612v0a.75.75 0 01-.75.75H9.75a.75.75 0 01-.75-.75v0c0-.212.03-.418.084-.612m7.332 0c.646.049 1.288.11 1.927.184 1.1.128 1.907 1.077 1.907 2.185V19.5a2.25 2.25 0 01-2.25 2.25H6.75A2.25 2.25 0 014.5 19.5V6.257c0-1.108.806-2.057 1.907-2.185a48.208 48.208 0 011.927-.184"
                                    />
                                </svg>
                                Copy
                            {/if}
                        </button>
                    </div>
                </div>

                <!-- Steps -->
                <div class="space-y-2">
                    <p
                        class="text-xs text-cream-muted/50 uppercase tracking-wider mb-3"
                    >
                        Quick Steps
                    </p>
                    <div class="flex items-start gap-3">
                        <span class="pixel-label text-green-400/60 mt-0.5"
                            >01</span
                        >
                        <span class="text-sm text-cream-muted"
                            >Open Minecraft Java Edition</span
                        >
                    </div>
                    <div class="flex items-start gap-3">
                        <span class="pixel-label text-green-400/60 mt-0.5"
                            >02</span
                        >
                        <span class="text-sm text-cream-muted"
                            >Click Multiplayer → Add Server</span
                        >
                    </div>
                    <div class="flex items-start gap-3">
                        <span class="pixel-label text-green-400/60 mt-0.5"
                            >03</span
                        >
                        <span class="text-sm text-cream-muted"
                            >Paste the IP and join</span
                        >
                    </div>
                </div>
            </div>
        </div>

        <!-- Bedrock Edition Card -->
        <div
            class="glass-card p-5 sm:p-8 hover:glass-card-hover group relative overflow-hidden"
        >
            <div
                class="absolute top-0 right-0 w-24 h-24 bg-gradient-to-bl from-sky-400/10 to-transparent rounded-bl-3xl"
            ></div>

            <div class="relative">
                <div class="flex items-center gap-3 sm:gap-4 mb-5 sm:mb-6">
                    <div
                        class="w-12 h-12 sm:w-14 sm:h-14 rounded-xl bg-sky-500/20 flex items-center justify-center
                      border border-sky-500/20 group-hover:border-sky-400/40 transition-colors"
                    >
                        <svg
                            class="w-6 h-6 sm:w-7 sm:h-7 text-sky-300"
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
                        <h3 class="text-lg sm:text-xl font-bold text-cream">
                            Bedrock Edition
                        </h3>
                        <p class="text-sm text-cream-muted/60">
                            Mobile / Console / Windows 10
                        </p>
                    </div>
                </div>

                <!-- Server IP -->
                <div class="mb-6">
                    <p
                        class="text-xs text-cream-muted/50 uppercase tracking-wider mb-2 block"
                        >Server Address</p
                    >
                    <div class="grid grid-cols-[minmax(0,1fr)_auto_auto] gap-2">
                        <div
                            class="bg-surface-primary/60 rounded-lg px-4 py-3 font-mono text-sky-300 text-sm break-all
                        border border-sky-500/20"
                        >
                            mc.lekkerboys.co.za
                        </div>
                        <div
                            class="bg-surface-primary/60 rounded-lg px-4 py-3 font-mono text-sky-300 text-sm
                      border border-sky-500/20"
                        >
                            25565
                        </div>
                        <button
                            onclick={() =>
                                copyToClipboard(
                                    "mc.lekkerboys.co.za:25565",
                                    "bedrock",
                                )}
                            class="px-4 py-3 bg-sky-500/20 hover:bg-sky-500/30 rounded-lg
                     text-sky-300 text-sm font-medium transition-all duration-200
                     border border-sky-500/20 hover:border-sky-400/40
                     flex items-center gap-2 justify-center"
                        >
                            {#if copiedBedrock}
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
                                        d="M4.5 12.75l6 6 9-13.5"
                                    />
                                </svg>
                                Copied!
                            {:else}
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
                                        d="M15.666 3.888A2.25 2.25 0 0013.5 2.25h-3c-1.03 0-1.9.693-2.166 1.638m7.332 0c.055.194.084.4.084.612v0a.75.75 0 01-.75.75H9.75a.75.75 0 01-.75-.75v0c0-.212.03-.418.084-.612m7.332 0c.646.049 1.288.11 1.927.184 1.1.128 1.907 1.077 1.907 2.185V19.5a2.25 2.25 0 01-2.25 2.25H6.75A2.25 2.25 0 014.5 19.5V6.257c0-1.108.806-2.057 1.907-2.185a48.208 48.208 0 011.927-.184"
                                    />
                                </svg>
                                Copy
                            {/if}
                        </button>
                    </div>
                </div>

                <!-- Steps -->
                <div class="space-y-2">
                    <p
                        class="text-xs text-cream-muted/50 uppercase tracking-wider mb-3"
                    >
                        Quick Steps
                    </p>
                    <div class="flex items-start gap-3">
                        <span class="pixel-label text-sky-400/60 mt-0.5"
                            >01</span
                        >
                        <span class="text-sm text-cream-muted"
                            >Open Minecraft Bedrock Edition</span
                        >
                    </div>
                    <div class="flex items-start gap-3">
                        <span class="pixel-label text-sky-400/60 mt-0.5"
                            >02</span
                        >
                        <span class="text-sm text-cream-muted"
                            >Go to Servers → Add Server</span
                        >
                    </div>
                    <div class="flex items-start gap-3">
                        <span class="pixel-label text-sky-400/60 mt-0.5"
                            >03</span
                        >
                        <span class="text-sm text-cream-muted"
                            >Enter IP and port 25565</span
                        >
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>

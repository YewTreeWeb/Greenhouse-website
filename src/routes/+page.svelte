<script lang="ts">
  import Nav from '$lib/components/Nav.svelte';
  import Hero from '$lib/components/Hero.svelte';
  import Ecosystem from '$lib/components/Ecosystem.svelte';
  import GlassCard from '$lib/components/GlassCard.svelte';

  let { toggleTheme, theme }: { toggleTheme: () => void; theme: string } = $props();

  const installCmds: Record<string, string[]> = {
    npm:  ['npm install -g @greenhouse/cli',  'greenhouse botanist', 'sprout my-app --stack vite', 'greenhouse sunroom'],
    pnpm: ['pnpm add -g @greenhouse/cli',     'greenhouse botanist', 'sprout my-app --stack vite', 'greenhouse sunroom'],
    bun:  ['bun add -g @greenhouse/cli',      'greenhouse botanist', 'sprout my-app --stack vite', 'greenhouse sunroom'],
    brew: ['brew install greenhouse',          'greenhouse botanist', 'sprout my-app --stack vite', 'greenhouse sunroom'],
  };

  let activeTab = $state('npm');

  const botanistRows = [
    { status: 'ok',   label: 'Node.js',          val: 'v20.11.0' },
    { status: 'ok',   label: 'Git',               val: '2.43.0' },
    { status: 'ok',   label: 'Bun',               val: '1.1.3' },
    { status: 'ok',   label: 'pnpm',              val: '9.1.0' },
    { status: 'warn', label: 'Deno',              val: 'not found', fix: '→ brew install deno' },
    { status: 'ok',   label: 'Docker',            val: '25.0.3' },
    { status: 'fail', label: 'Laravel installer', val: 'not found', fix: '→ composer global req' },
    { status: 'ok',   label: 'Git identity',      val: 'Mat Teague' },
  ] as const;
</script>

<Nav {theme} onToggle={toggleTheme} />

<main class="max-w-[1100px] mx-auto px-8 relative z-10">

  <Hero />
  <hr class="gh-divider" />

  <Ecosystem />
  <hr class="gh-divider" />

  <!-- Features -->
  <section id="features" class="py-20">
    <div class="section-label">// why greenhouse</div>
    <h2 class="font-display font-bold text-gh-text mb-4 leading-[1.15]"
        style="font-size: var(--text-section)">
      Built for how you<br />actually work
    </h2>
    <p class="text-[17px] text-gh-secondary font-light leading-relaxed max-w-xl mb-12">
      No opinions forced on you. Every tool runs standalone. Every decision is yours.
    </p>

    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
      <GlassCard padding="lg" hoverable>
        <div class="w-10 h-10 rounded-[9px] flex items-center justify-center text-lg mb-4"
             style="background:rgba(123,201,84,0.1);border:1px solid rgba(123,201,84,0.2)">🔀</div>
        <h3 class="font-display text-xl text-gh-text mb-2">Runtime agnostic</h3>
        <p class="text-sm text-gh-secondary font-light leading-relaxed">
          Greenhouse detects Node, Bun, or pnpm automatically. A Deno + Cliffy version is in active development.
        </p>
      </GlassCard>

      <GlassCard padding="lg" hoverable>
        <div class="w-10 h-10 rounded-[9px] flex items-center justify-center text-lg mb-4"
             style="background:rgba(212,145,74,0.1);border:1px solid rgba(212,145,74,0.2)">🔬</div>
        <h3 class="font-display text-xl text-gh-text mb-2">Botanist — health check</h3>
        <p class="text-sm text-gh-secondary font-light leading-relaxed">
          Inspect your full environment. Green, amber, red per tool with exact fix commands —
          inspired by <code class="font-mono text-xs text-gh-green">flutter doctor</code>.
        </p>
      </GlassCard>

      <GlassCard padding="lg" hoverable>
        <div class="w-10 h-10 rounded-[9px] flex items-center justify-center text-lg mb-4"
             style="background:rgba(123,201,84,0.1);border:1px solid rgba(123,201,84,0.2)">📸</div>
        <h3 class="font-display text-xl text-gh-text mb-2">Git-backed snapshots</h3>
        <p class="text-sm text-gh-secondary font-light leading-relaxed">
          Seedbank commits project manifests to your chosen destination — local, GitHub, or NAS.
          Restore any project to any date without storing node_modules.
        </p>
      </GlassCard>

      <GlassCard padding="lg" hoverable>
        <div class="w-10 h-10 rounded-[9px] flex items-center justify-center text-lg mb-4"
             style="background:rgba(212,145,74,0.1);border:1px solid rgba(212,145,74,0.2)">🖥</div>
        <h3 class="font-display text-xl text-gh-text mb-2">Tauri desktop app</h3>
        <p class="text-sm text-gh-secondary font-light leading-relaxed">
          Sunroom ships as a native macOS tray app — 8MB, no Chromium. Trigger commands and
          stream live logs without a terminal.
        </p>
      </GlassCard>

      <!-- Gardener — full width -->
      <div class="md:col-span-2">
        <GlassCard padding="lg" hoverable>
          <div class="pending-pill">● coming soon</div>
          <div class="w-10 h-10 rounded-[9px] flex items-center justify-center text-lg mb-4"
               style="background:rgba(167,139,250,0.1);border:1px solid rgba(167,139,250,0.2)">🌿</div>
          <h3 class="font-display text-xl text-gh-violet mb-2">Gardener — AI project intelligence</h3>
          <p class="text-sm text-gh-secondary font-light leading-relaxed mb-4">
            The only Greenhouse tool that watches rather than waits. Powered entirely by your
            local Ollama instance. No data leaves your machine.
          </p>
          <div class="flex flex-col gap-2">
            {#each [
              'gardener ask "which of my projects is most out of date?"',
              'gardener ask "what should I work on first today?"',
              'gardener insights',
              'gardener report',
            ] as cmd}
              <div class="font-mono text-xs text-gh-violet rounded-lg px-3 py-2"
                   style="background:rgba(167,139,250,0.05);border:1px solid rgba(167,139,250,0.15)">
                <span class="text-gh-muted mr-1.5">$</span>{cmd}
              </div>
            {/each}
          </div>
        </GlassCard>
      </div>
    </div>
  </section>

  <hr class="gh-divider" />

  <!-- Runtimes -->
  <section class="py-20">
    <div class="section-label">// runtimes</div>
    <h2 class="font-display font-bold text-gh-text mb-4 leading-[1.15]"
        style="font-size: var(--text-section)">
      Your tools, your runtime
    </h2>
    <p class="text-[17px] text-gh-secondary font-light leading-relaxed max-w-xl mb-8">
      Greenhouse works with whatever you have. No lock-in.
    </p>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
      {#each [
        { badge: 'active',  name: 'Node.js', desc: 'Primary runtime. Oclif + Clack. Requires Node 18+.' },
        { badge: 'active',  name: 'Bun',     desc: 'Auto-detected when bun.lockb is present. Drop-in compatible.' },
        { badge: 'planned', name: 'Deno',    desc: 'Cliffy-based port. Install from JSR. Built-in test runner.' },
      ] as runtime}
        <GlassCard hoverable>
          <div class="text-center p-1">
            <span class="runtime-badge-{runtime.badge}">{runtime.badge}</span>
            <div class="font-display text-[22px] text-gh-text mb-1.5">{runtime.name}</div>
            <div class="text-[13px] text-gh-muted leading-relaxed">{runtime.desc}</div>
          </div>
        </GlassCard>
      {/each}
    </div>
  </section>

  <hr class="gh-divider" />

  <!-- Install + Botanist -->
  <section id="install" class="py-20">
    <div class="grid grid-cols-1 md:grid-cols-2 gap-16 items-start">

      <div>
        <div class="section-label">// install</div>
        <h2 class="font-display font-bold text-gh-text mb-4 leading-[1.15]"
            style="font-size: var(--text-section)">
          One line to<br />start growing
        </h2>
        <p class="text-[17px] text-gh-secondary font-light leading-relaxed mb-8">
          Install globally and every tool is immediately available — umbrella command or standalone alias.
        </p>

        <div class="glass-card overflow-hidden">
          <!-- Tabs -->
          <div class="flex border-b px-4"
               style="border-color:var(--glass-border);background:rgba(255,255,255,0.02)">
            {#each Object.keys(installCmds) as tab}
              <button
                onclick={() => activeTab = tab}
                class="font-mono text-xs px-3.5 py-3 cursor-pointer bg-transparent
                       border-0 border-b-2 transition-colors
                       {activeTab === tab
                         ? 'text-gh-green border-gh-green'
                         : 'text-gh-muted border-transparent'}"
              >{tab}</button>
            {/each}
          </div>
          <!-- Code -->
          <div class="p-6 font-mono text-sm text-gh-green leading-loose">
            {#each installCmds[activeTab] as line}
              <div><span class="text-gh-muted">$</span> {line}</div>
            {/each}
          </div>
        </div>
      </div>

      <div>
        <div class="section-label">// botanist</div>
        <h2 class="font-display font-bold text-gh-text mb-4 leading-[1.15]"
            style="font-size: var(--text-section)">
          Full environment<br />health check
        </h2>
        <p class="text-[17px] text-gh-secondary font-light leading-relaxed mb-6">
          Run <code class="font-mono text-[13px] text-gh-green">greenhouse botanist</code> any
          time — every tool inspected and reported.
        </p>

        <GlassCard>
          <div class="font-mono text-[13px] space-y-1 p-1">
            {#each botanistRows as row}
              <div class="flex items-center gap-3 py-1">
                <span class="w-4 text-center
                  {row.status === 'ok'   ? 'text-terminal-green'  :
                   row.status === 'warn' ? 'text-terminal-yellow' :
                                          'text-terminal-red'}">
                  {row.status === 'ok' ? '✓' : row.status === 'warn' ? '!' : '✗'}
                </span>
                <span class="text-gh-secondary min-w-[150px]">{row.label}</span>
                <span class="text-xs
                  {row.status === 'fail' ? 'text-terminal-red'    :
                   row.status === 'warn' ? 'text-gh-amber'        :
                                          'text-gh-muted'}">
                  {row.val}
                </span>
                {#if 'fix' in row}
                  <span class="text-terminal-flag text-[11px] ml-auto">{row.fix}</span>
                {/if}
              </div>
            {/each}
            <div class="pt-3 mt-2 text-xs text-gh-muted border-t"
                 style="border-color:var(--glass-border)">
              1 issue · 1 warning — run fix commands above
            </div>
          </div>
        </GlassCard>
      </div>

    </div>
  </section>

</main>

<footer class="border-t mt-10 py-10" style="border-color:var(--glass-border)">
  <div class="max-w-[1100px] mx-auto px-8 flex items-center justify-between">
    <span class="text-[13px] text-gh-muted">MIT © 2026 Mat Teague · Part of the Greenhouse Ecosystem</span>
    <div class="flex gap-6">
      {#each [['GitHub','https://github.com/YewTreeWeb/greenhouse-project'],['Docs','#install'],['Changelog','https://github.com/YewTreeWeb/greenhouse-project/blob/main/CHANGELOG.md']] as [label,href]}
        <a {href} target={href.startsWith('http') ? '_blank' : undefined} rel="noopener"
           class="text-[13px] text-gh-muted no-underline hover:text-gh-secondary transition-colors">
          {label}
        </a>
      {/each}
    </div>
  </div>
</footer>

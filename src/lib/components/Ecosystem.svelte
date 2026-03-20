<script lang="ts">
  import GlassCard from './GlassCard.svelte';

  const tools: { icon: string; name: string; desc: string; tag: string; variant: string; pending?: boolean }[] = [
    { icon: '🏡', name: 'terrarium', desc: 'System setup with Nix + Homebrew. Reproducible environments and dotfiles.',            tag: 'system',      variant: 'green'  },
    { icon: '🌱', name: 'sprout',    desc: 'Scaffold new projects. Vite, Astro, Laravel 12 with official starter kits.',           tag: 'scaffold',    variant: 'green'  },
    { icon: '🌾', name: 'cultivate', desc: 'Apply dev configs. ESLint, Prettier, Tailwind presets in one command.',                tag: 'config',      variant: 'green'  },
    { icon: '🌸', name: 'bud',       desc: 'Spin up sandboxes. Docker isolation with TTL-based auto-teardown.',                   tag: 'sandbox',     variant: 'amber'  },
    { icon: '🍂', name: 'harvest',   desc: 'Build and export production artifacts. Package for deployment.',                       tag: 'build',       variant: 'green'  },
    { icon: '🌰', name: 'seedbank',  desc: 'Git-backed project snapshots. Version and restore your entire dev state.',             tag: 'backup',      variant: 'amber'  },
    { icon: '🪴', name: 'planter',   desc: 'Restore projects from Seedbank snapshots. Plants the seeds back.',                     tag: 'restore',     variant: 'violet' },
    { icon: '💧', name: 'water',     desc: 'Update dependencies and system packages. Keep everything fresh.',                      tag: 'maintenance', variant: 'green'  },
    { icon: '✂️', name: 'prune',     desc: 'Remove old caches, unused branches, and dead dependencies.',                          tag: 'cleanup',     variant: 'green'  },
    { icon: '🔬', name: 'botanist',  desc: 'Full environment health check. Green, amber, red per tool with fix hints.',            tag: 'diagnostic',  variant: 'green'  },
    { icon: '☀️', name: 'sunroom',   desc: 'Tauri-powered desktop dashboard to manage the entire ecosystem.',                     tag: 'dashboard',   variant: 'amber'  },
    { icon: '🌿', name: 'gardener',  desc: 'AI project intelligence. Watches all projects, surfaces insights via Ollama.',         tag: '● pending',   variant: 'violet', pending: true },
  ];
</script>

<section id="ecosystem" class="py-20">
  <div class="section-label">// ecosystem</div>
  <h2 class="font-display font-bold text-gh-text mb-4 leading-[1.15]"
      style="font-size: var(--text-section)">
    Every tool has its <em class="italic text-gh-green">season</em>
  </h2>
  <p class="text-[17px] text-gh-secondary font-light leading-relaxed max-w-xl mb-12">
    Each CLI handles one phase of your workflow. Every one runs standalone or under the umbrella.
    Dashed border = coming soon.
  </p>

  <div class="grid grid-cols-2 md:grid-cols-3 gap-3">
    {#each tools as tool}
      <GlassCard hoverable pending={tool.pending ?? false}>
        <span class="text-[22px] mb-2.5 block" aria-hidden="true">{tool.icon}</span>
        <div class="font-mono text-sm font-medium mb-1.5
                    {tool.pending ? 'text-gh-muted' : 'text-gh-green'}">
          {tool.name}
        </div>
        <div class="text-[13px] text-gh-muted leading-relaxed">{tool.desc}</div>
        <span class="eco-tag-{tool.variant}">{tool.tag}</span>
      </GlassCard>
    {/each}
  </div>
</section>

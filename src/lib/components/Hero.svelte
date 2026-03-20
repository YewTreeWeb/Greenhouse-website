<section class="pt-24 pb-20 relative">
  <div class="grid grid-cols-1 md:grid-cols-2 gap-16 items-center">

    <!-- Copy -->
    <div>
      <div class="section-label flex items-center gap-2
                  before:content-[''] before:inline-block before:w-6 before:h-px before:bg-gh-green">
        CLI ecosystem
      </div>

      <h1 class="font-display font-bold text-gh-text mb-6 leading-[1.1]"
          style="font-size: var(--text-hero)">
        Nurture your<br />
        <em class="italic text-gh-green">development</em><br />
        environment
      </h1>

      <p class="text-[17px] text-gh-secondary font-light leading-relaxed mb-10">
        A modular suite of CLI tools for planting, cultivating, and harvesting
        your dev projects — from system setup to production builds.
      </p>

      <div class="flex gap-3 flex-wrap mb-8">
        <a href="#install" class="btn-large-primary">Install Greenhouse</a>
        <a href="#ecosystem" class="btn-large-secondary">Read the docs</a>
      </div>

      <div class="flex gap-10">
        {#each [['15', 'CLI tools'], ['3', 'runtimes'], ['1', 'command to start']] as [val, label]}
          <div>
            <div class="font-display text-[30px] text-gh-text leading-none">{val}</div>
            <div class="text-[12px] text-gh-muted tracking-wide mt-1">{label}</div>
          </div>
        {/each}
      </div>
    </div>

    <!-- Terminal -->
    <div class="glass-terminal font-mono text-[13px]" aria-label="Terminal demo">
      <div class="flex items-center gap-1.5 px-4 py-2.5 border-b"
           style="border-color: var(--glass-border); background: rgba(255,255,255,0.03)">
        <div class="w-2.5 h-2.5 rounded-full bg-terminal-red"></div>
        <div class="w-2.5 h-2.5 rounded-full bg-terminal-yellow"></div>
        <div class="w-2.5 h-2.5 rounded-full bg-terminal-green"></div>
        <span class="ml-auto text-[11px] text-gh-muted tracking-wider">zsh — greenhouse</span>
      </div>

      <div class="p-5 leading-loose">
        <div>
          <span class="text-gh-amber">→</span>
          <span class="text-gh-green"> greenhouse sprout</span>
          <span class="text-terminal-flag"> my-app --stack laravel --framework react</span>
        </div>
        <div class="pl-4 text-[12px] text-gh-green/55">🌱  Creating Laravel project: my-app</div>
        <div class="pl-4 text-[12px] text-gh-green">✅  Project ready at ./my-app</div>
        <br />
        <div>
          <span class="text-gh-amber">→</span>
          <span class="text-gh-green"> greenhouse botanist</span>
        </div>
        <div class="pl-4 text-[12px] text-gh-green">✅  Node.js          v20.11.0</div>
        <div class="pl-4 text-[12px] text-gh-amber">⚠   Deno             not found → brew install deno</div>
        <div class="pl-4 text-[12px] text-gh-green">✅  Docker           25.0.3</div>
        <br />
        <div>
          <span class="text-gh-amber">→</span>
          <span class="text-gh-green"> gardener ask</span>
          <span class="text-terminal-flag"> "what needs attention today?"</span>
        </div>
        <div class="pl-4 text-[12px] text-gh-violet/60">🌿  3 projects analysed via local LLM...</div>
        <div class="pl-4 text-[12px] text-gh-violet/60">💡  frontend: 4 deps with security advisories</div>
        <div>
          <span class="text-gh-muted">_</span>
          <span class="inline-block w-2 h-3.5 bg-gh-green animate-blink align-middle ml-0.5"></span>
        </div>
      </div>
    </div>

  </div>
</section>

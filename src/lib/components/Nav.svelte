<script lang="ts">
  interface Props { theme: string; onToggle: () => void; }
  let { theme, onToggle }: Props = $props();
</script>

<nav class="glass-nav sticky top-0 z-50 px-8">
  <div class="max-w-[1100px] mx-auto flex items-center justify-between h-[60px]">

    <a href="/" class="font-display text-xl text-gh-text flex items-center gap-2.5 no-underline">
      <div
        class="w-7 h-7 bg-gh-green rounded-[50%_50%_50%_10%] rotate-[-30deg] shrink-0"
        style="box-shadow: var(--shadow-glow-leaf)"
        aria-hidden="true"
      ></div>
      Greenhouse
    </a>

    <ul class="hidden md:flex items-center gap-8 list-none m-0 p-0">
      <li><a href="#ecosystem" class="text-gh-secondary text-sm no-underline hover:text-gh-text transition-colors">Ecosystem</a></li>
      <li><a href="#install"   class="text-gh-secondary text-sm no-underline hover:text-gh-text transition-colors">Docs</a></li>
      <li><a href="#install"   class="text-gh-secondary text-sm no-underline hover:text-gh-text transition-colors">Sunroom</a></li>
    </ul>

    <div class="flex items-center gap-2.5">
      <button
        onclick={onToggle}
        aria-label="Toggle theme"
        class="btn-ghost w-[34px] h-[34px] flex items-center justify-center p-0 text-[15px]"
      >
        {theme === 'dark' ? '☀' : '☾'}
      </button>
      <a href="https://github.com/YewTreeWeb/greenhouse-project" target="_blank" rel="noopener" class="btn-ghost hidden sm:inline-block">
        View on GitHub
      </a>
      <a href="#install" class="btn-primary">Get started</a>
    </div>

  </div>
</nav>

<script lang="ts">
  import '../app.css';
  import { onMount } from 'svelte';
  import type { Snippet } from 'svelte';

  let theme = $state('dark');

  onMount(() => {
    const stored = localStorage.getItem('gh-theme') ?? 'dark';
    theme = stored;
    document.documentElement.setAttribute('data-theme', theme);
  });

  function toggleTheme() {
    theme = theme === 'dark' ? 'light' : 'dark';
    document.documentElement.setAttribute('data-theme', theme);
    localStorage.setItem('gh-theme', theme);
  }

  let { children }: { children: Snippet<[{ toggleTheme: () => void; theme: string }]> } = $props();
</script>

<!-- Ambient orbs -->
<div class="fixed inset-0 pointer-events-none z-0 overflow-hidden" aria-hidden="true">
  <div class="orb orb-1"></div>
  <div class="orb orb-2"></div>
  <div class="orb orb-3"></div>
</div>

{@render children({ toggleTheme, theme })}

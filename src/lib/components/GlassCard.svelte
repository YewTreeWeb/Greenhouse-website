<script lang="ts">
  interface Props {
    padding?: 'sm' | 'md' | 'lg';
    hoverable?: boolean;
    pending?: boolean;
    class?: string;
    children?: import('svelte').Snippet;
  }

  let {
    padding = 'md',
    hoverable = true,
    pending = false,
    class: className = '',
    children,
  }: Props = $props();

  const padMap: Record<string, string> = {
    sm: 'p-4',
    md: 'p-6',
    lg: 'p-7',
  };
</script>

<div class="glass-card {hoverable ? 'hoverable' : ''} {pending ? 'pending' : ''} {padMap[padding]} {className}">
  {#if children}
    {@render children()}
  {/if}
</div>

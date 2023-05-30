<script lang="ts">
  import { onMount } from 'svelte';
  import LucideIcon from './lucide-icon.svelte';

  const themes = ['light', 'dark'];
  let theme = '';
  let rootEl: HTMLElement | null = null;

  onMount(() => {
    rootEl = document.documentElement;
    if (localStorage && localStorage.getItem('theme')) {
      theme = localStorage.getItem('theme') || '';
    } else if (window && window.matchMedia('(prefers-color-scheme: dark)').matches) {
      theme = 'dark';
    }
  });

  function handleChange(event: Event) {
    theme = (event.target as HTMLInputElement).value;
    localStorage.setItem('theme', theme);
  }

  $: if (rootEl && theme === 'light') {
    rootEl.classList.remove('dark');
  } else if (rootEl && theme === 'dark') {
    rootEl.classList.add('dark');
  }
</script>

<div class="flex gap-1 absolute top-8 right-0">
  {#each themes as t}
    <label class={`cursor-pointer ${theme === t ? 'bg-foreground text-background rounded-full p-[5px]' : 'text-foreground bg-transparent rounded-full p-[5px]'}`}>
      <LucideIcon 
        name={t ==="dark"?"Moon":"Sun"} 
        class="h-4 w-4"
      />
      <input
        class="hidden"
        type="radio"
        name="theme-toggle"
        checked={theme === t}
        value={t}
        title={`Use ${t} theme`}
        aria-label={`Use ${t} theme`}
        on:change={handleChange}
      />
    </label>
  {/each}
</div>

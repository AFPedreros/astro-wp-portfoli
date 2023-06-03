<script lang="ts">
	import * as icons from 'lucide-svelte';
	type IconName = 'Sun' | 'Moon'|"Github"|"Twitter"|"Linkedin"| "ArrowUpRight" ;
	export let name: IconName;
</script>

<svelte:component this={icons[name]} {...$$props} />
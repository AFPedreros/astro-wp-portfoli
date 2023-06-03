<script lang="ts">
    import Span from "./badge.svelte"
    import LucideIcon from "./lucide-icon.svelte"
    
    let variant: "experience" | "project";
    export { variant };
</script>

<div class="relative hover:bg-foreground/5 group transition-colors duration-200 hover:cursor-pointer md:flex gap-4 md:p-4 rounded-md">
    <LucideIcon name="ArrowUpRight" class="absolute top-4 right-4 duration-200 opacity-0 group-hover:opacity-100 h-6 w-6 group-hover:text-primary cursor-pointer transition-opacity" />
    {#if variant === "experience"}
        <h3 class="text-sm font-medium whitespace-nowrap">FEB - PRESENT</h3>
    {:else if variant === "project"}
        <img class="w-48 md:h-12 mb-8 md:mb-0 object-cover rounded-md" src="https://brittanychiang.com/_next/image?url=%2Fimages%2Fprojects%2Fcourse-card.png&w=256&q=75" alt="">
    {/if}
    <div>
        <h3 class="mb-3 text-foreground hover:text-primary transition-colors duration-200 group-hover:text-primary">Front-end Developer at Partner</h3>
        <p class="mb-3">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Ut et massa mi. Aliquam in hendrerit urna. Pellentesque sit amet sapien fringilla, mattis ligula consectetur, ultrices
            mauris. Maecenas vitae mattis tellus.
        </p>
        <div>
            <Span>Nextjs</Span>
        </div>
    </div>
</div>

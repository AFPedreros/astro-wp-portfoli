<script lang="ts">
    let items = ['About', 'Experience', 'Projects'];
    let activeItem = '';

    if (typeof window !== 'undefined') {
        window.addEventListener('reset', () => {
            activeItem = '';
        });
    }
</script>

<nav class="hidden lg:block">
    <ul class="flex items-start flex-col gap-4 text-lg text-secondary">
    {#each items as item (item)}
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <li>
        <a 
            class="group flex gap-5 items-center toggle-item {activeItem === item ? 'text-primary' : 'text-secondary'}"
            on:click={() => {activeItem = item}}
            href={`#${item.toLowerCase()}`}
        >
            <div 
                class="{activeItem === item ? 'w-20' : 'w-10'} h-[1px] mt-[2px] {activeItem === item ? 'bg-primary' : 'bg-secondary'} group-hover:bg-primary"
            ></div>
            <p class="group-hover:text-primary font-bold text-sm">{item.toLocaleUpperCase()}</p>
        </a>
    </li>
    {/each}
</ul>
</nav>

<script lang="ts">
    import { onMount } from "svelte";
    
    let x = 0;
    let y = 0;
    let pointerMoved = false;
    
    function handleMouseMove(event: MouseEvent) {
        x = event.clientX;
        y = event.clientY;
        
        if (!pointerMoved) {
            pointerMoved = true;
        }
    }
    
    onMount(() => {
        document.addEventListener("mousemove", handleMouseMove);
        
        return () => {
            document.removeEventListener("mousemove", handleMouseMove);
        };
    });
</script>

<style>
    .spotlight {
        position: absolute;
        top: 0;
        left: 0;
        pointer-events: none;
        width: 100%;
        height: 100%;
        overflow: hidden;
    }

    .light {
        position: absolute;
        transform: translate(-50%, -50%);
        width: 700px;
        height: 700px;
        border-radius: 50%;
        background: radial-gradient(circle, rgba(255, 255, 255, 0.07), transparent 70%);
        pointer-events: none;
        mix-blend-mode: screen;
        opacity: 0.8;
        transition: opacity 0.2s ease-out;
    }
</style>
  
{#if pointerMoved}
    <div class="spotlight hidden md:block">
        <div class="light" style="top: {y}px; left: {x}px;"></div>
    </div>
{/if}

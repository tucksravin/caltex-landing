<script lang="ts">
    let { href = "", onclick, class:passedClasses = '', children, isWhite=false, ...others  } = $props();

    let baseClasses = $state("rounded border-2 border-solid border-dark px-10 pt-4 pb-3 h-fit hover:bg-dark hover:text-white transition")
    if(isWhite)
        baseClasses="rounded text-white border-2 border-solid border-white px-10 pt-4 pb-3 h-fit hover:bg-white hover:text-dark transition"

</script>

<style>
    a, button{
    cursor: pointer;
    font-size: 12px;
    font-style: normal;
    font-weight: 700;
    line-height: normal;
    letter-spacing: 1px;
    text-transform: uppercase;
}
</style>


<div class="bump">
    {#if href}
        <a 
            {href} 
            {onclick} 
            class="{baseClasses} {passedClasses}">
                {@render children()}
        </a>
    {:else}
    <button {onclick}
            class="{baseClasses} {passedClasses}">
            {@render children()}
    </button>
    {/if}
</div>
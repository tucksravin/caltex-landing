<!-- @migration-task Error while migrating Svelte code: $$props is used together with named props in a way that cannot be automatically migrated. -->
<!-- @migration-task Error while migrating Svelte code: $$props is used together with named props in a way that cannot be automatically migrated. -->
<script lang="ts">
    import placeholder from "$lib/assets/images/image_placeholder.svg"

    export let src = placeholder;
    export let alt = "placeholder"


    const rotationAngle = "45";
    let crossLength = "141%";
</script>

<div class="w-full my-8 {$$props.class || ''}">
    <div class="w-full aspect-square {src===placeholder ? "border-light border-2 bg-light bg-opacity-25":""}  rounded-sm  flex items-center justify-center relative">
        <img {src} {alt} class="z-10 {src==placeholder ? "w-16 bg-[#F2F5F7]" : "w-full"}"/>
        <div class="absolute bg-light h-[2px] {src===placeholder ? "":"hidden"}" style="transform: rotate({rotationAngle}deg); width:{crossLength}"></div>
        <div class="absolute bg-light h-[2px] {src===placeholder ? "":"hidden"}" style="transform: rotate(-{rotationAngle}deg); width:{crossLength}"></div>
    </div>
</div>
<script lang="ts">
    import profile_placeholder from "$lib/assets/images/profile_placeholder.jpeg"
    import logo_placeholder from "$lib/assets/icons/logos/logo.svg"
    

    interface Props {
        src?: any;
        alt?: string;
        href?: string;
        name?: string;
        title?: string;
        socials?: any;
    }

    let {
        src = profile_placeholder,
        alt = "profile picture placeholder",
        href = "",
        name = "",
        title = "",
        socials = [{
        platform: "",
        href:""
                        }]
    }: Props = $props();

    
</script>

{#if href}
<div class="w-full h-full relative">
    <a {href} class="absolute z-0 top-0 left-0 w-full h-full" aria-label={title}></a>
    <img {src} {alt} class="w-full h-full object-cover"/>
    <div class="w-full h-full absolute top-0 left-0 flex flex-col items-center justify-center bg-dark opacity-0 hover:opacity-100 hover:bg-opacity-75 transition-all duration-500 ease-fast-slow">
        <div class="h-2"></div>
        <h5 class="text-white my-3">{name}</h5>
        <p class="text-light my-3">{title}</p>
        <div class="h-6 my-3 flex flex-row items center justify-center transition-opacity">
            {#each socials as social }
               
                <a href={social.href} class="mx-6 w-6 h-6 hover:opacity-75 transition-all bump z-10">
                    {#if social.platform==='facebook'}
                        <i class="fa-brands fa-facebook fa-2xl invert" ></i>
                    {:else if social.platform=='twitter'}
                    <i class="fa-brands fa-x fa-2xl invert" ></i>
                    {:else if social.platform=='redit'}
                    <i class="fa-brands fa-redit fa-2xl invert" ></i>
                    {:else if social.platform=='instagram'}
                        <i class="fa-brands fa-instagram fa-2xl invert" ></i>
                    {/if}

                </a>
               
            {/each}
        </div>
    </div>
</div>

 {:else}
<div class="w-full h-full relative">
    <img {src} {alt} class="w-full h-full object-cover"/>
    <div class="w-full h-full absolute top-0 left-0 flex flex-col items-center justify-center bg-dark opacity-0 hover:opacity-100 hover:bg-opacity-75 transition-all duration-500 ease-fast-slow">
        <div class="h-2"></div>
        <h5 class="text-white my-3">{name}</h5>
        <p class="text-light my-3">{title}</p>
        <div class="h-6 my-3 flex flex-row items center justify-center ">
            {#each socials as social }
            <a href={social.href} class="mx-6 w-6 h-6 hover:opacity-75 transition-all bump">
                {#if social.platform==='facebook'}
                    <i class="fa-brands fa-facebook fa-2xl invert" ></i>
                {:else if social.platform=='twitter'}
                <i class="fa-brands fa-facebook fa-2xl invert" ></i>
                {:else if social.platform=='redit'}
                <i class="fa-brands fa-facebook fa-2xl invert" ></i>
                {:else if social.platform=='instagram'}
                    <i class="fa-brands fa-facebook fa-2xl invert" ></i>
                {/if}

            </a>

            {/each}
        </div>
    </div>
</div>
 {/if}
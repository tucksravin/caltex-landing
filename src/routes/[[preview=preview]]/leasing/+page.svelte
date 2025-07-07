<script lang='ts'>
import ContentWidth from "$lib/components/ContentWidth/ContentWidth.svelte";
import { PrismicImage } from "@prismicio/svelte";

 let { data } = $props();
  let content = $state(data.page.data);
  $effect(() => { data; content = data.page.data });
</script>

<ContentWidth class='gap-20 flex flex-col items-start pt-48'>
    <h1>AED LEASING</h1>
</ContentWidth>

<section id="s2" class="w-screen mt-20 lg:mt-52">
  <ContentWidth class="flex flex-col items-start justify-start gap-8 lg:gap-12">
    <h3 class="text-dark md:w-1/3">{content.s2_eyebrow}</h3>
    <div class="w-full flex justify-between flex-wrap">
      {#each content.s2_icons as icon, i}
        <div
          class="w-full md:w-1/2 pb-8 md:pb-10 {i % 2 == 0
            ? 'md:pr-5'
            : 'md:pl-5'}"
        >
          <div
            class="h-40 md:h-52 w-full bg-white text-primary flex flex-row justify-between items-center rounded-[7px] p-11 gap-11"
          >
            <PrismicImage class="w-32" field={icon.icon} />
            <h3>{icon.label}</h3>
          </div>
        </div>
      {/each}
    </div>

      <h5 class="text-dark">{content.s2_closing_text}</h5>

  </ContentWidth>
</section>
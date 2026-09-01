<script lang="ts">
  import ContentWidth from "$lib/components/ContentWidth/ContentWidth.svelte";
  import { PrismicImage, PrismicRichText } from "@prismicio/svelte";
  import { cappedWidths } from "@reddoorla/maintenance/images";

  let { data, ..._rest } = $props();
  let content = $derived(data.page.data);
</script>

<ContentWidth class="gap-20 flex flex-col items-start pt-48">
  <h1>Grants & Community</h1>
</ContentWidth>

<section id="s8" class="w-screen bg-primary text-white mt-24 py-16 md:py-24 -mb-48 relative">
  <ContentWidth class="flex flex-col md:flex-row">
    <div class="w-full md:w-1/2 flex flex-col items-start md:pr-5">
      <PrismicImage
        class="w-full"
        field={content.s8_title}
        widths={cappedWidths(content.s8_title)}
        sizes="(min-width: 768px) 44vw, 88vw"
        loading="eager"
        fetchpriority="high"
      />
      <PrismicImage
        class="w-2/3 -translate-x-[20%]"
        field={content.s8_aed}
        widths={cappedWidths(content.s8_aed)}
        sizes="(min-width: 768px) 29vw, 59vw"
        loading="eager"
        fetchpriority="high"
      />
    </div>
    <div class="w-full md:w-1/2 flex flex-col md:pl-5">
      <div class="rich-text mt-4 text-dark">
        <PrismicRichText field={content.s8_subheader} />
      </div>
      <div class="rich-text mt-8">
        <PrismicRichText field={content.s8_light_text} />
      </div>
    </div>
  </ContentWidth>
</section>

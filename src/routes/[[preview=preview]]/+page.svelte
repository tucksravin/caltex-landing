<script lang='ts'>
  import ContentWidth from "$lib/components/ContentWidth/ContentWidth.svelte";
	import ScreenWidthImage from "$lib/components/ScreenWidth/ScreenWidthImage.svelte";
  import { PrismicImage } from "@prismicio/svelte";
  import life from "$lib/assets/icons/LifeSaving.svg"
  import devices from "$lib/assets/icons/Devices.svg"
  import subtitle from "$lib/assets/icons/subtitle.svg"
  
	  let { data } = $props();
  
	  let viewpoortWidth=$state(1024)
  
	  const content = data.page.data
  </script>
  <style>
	.text{
		color: #131313;
		font-family: "Helvetica Neue LT Std", 'helvetica';
		font-size: 16px;
		font-style: normal;
		font-weight: 500;
		line-height: 1.66em; /* 166.667% */
	}
  </style>
  
  <svelte:window bind:innerWidth={viewpoortWidth} />
  
  <nav class="w-screen fixed top-0 left-0">
	<ContentWidth class="flex flex-row justify-between">
		<PrismicImage field={content.logo} class="h-10 mt-12" />
	</ContentWidth>
  </nav>
  {#if viewpoortWidth>768}
	  <ScreenWidthImage field={content.background_image} class="flex justify-between">
		<div class="w-2/3 flex flex-col justify-end items-start gap-12 pb-44">
			<img src={life} alt="life saving" class="h-20 xl:h-[165px]"/>
			<img src={devices} alt="devices" class="h-20 xl:h-[165px]"/>
			<img src={subtitle} alt="Protect Your Employees. Protect Your customers." class="mt-4"/>

		</div>
		<div class="flex flex-col justify-end items-end w-[30%] overflow-hidden">
			<div class="w-full flex flex-col items-center ">
				<PrismicImage field={content.aed} class="w-full -mb-36 z-10"/>
				<div class="bg-[#EA7724] text px-5 pt-48  pb-48 w-1/2">
					AEDs and Program Management Currently Serving the Texas Hill Country and San Antonio area.
				</div>
			</div>
		</div>
	  </ScreenWidthImage>
	  <footer class="h-32 w-screen bg-black -mt-32 z-20 relative">
		<ContentWidth class="h-full flex flex-col justify-center items-start gap-2">
			<div class="text-white">
				For information on an AED Program for Your Business or Organization:
			</div>
			<div class="text-white">
				Ryan Kohnen  |  210.273.7767  |  ryan@ryankohnen.com
			</div>
		</ContentWidth>
	  </footer>
  {:else}
  {/if}
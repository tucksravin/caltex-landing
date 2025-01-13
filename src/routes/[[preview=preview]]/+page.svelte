<script lang='ts'>
  import ContentWidth from "$lib/components/ContentWidth/ContentWidth.svelte";
	import ScreenWidthImage from "$lib/components/ScreenWidth/ScreenWidthImage.svelte";
  import { PrismicImage } from "@prismicio/svelte";
  import life from "$lib/assets/icons/LifeSaving.svg"
  import devices from "$lib/assets/icons/Devices.svg"
  import subtitle from "$lib/assets/icons/subtitle.svg"
  import mobileLife from "$lib/assets/icons/m_LifeSaving.svg"
  import mobileDevices from "$lib/assets/icons/m_devices.svg"
  
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
	.text-mobile{
		color: var(--black, #131313);
		font-family: "Helvetica Neue LT Std", 'helvetica';
		font-size: 20px;
		font-style: normal;
		font-weight: 500;
		line-height: 30px; /* 184.615% */

	}

	@media only screen and (max-width:786px) {
		.text-mobile{
		color: var(--black, #131313);
		font-family: "Helvetica Neue LT Std", 'helvetica';
		font-size: 13px;
		font-style: normal;
		font-weight: 500;
		line-height: 24px; /* 184.615% */

	}
	}

	
	.subtitle{
		color: var(--black, #131313);
font-family: "Helvetica Neue LT Std", 'helvetica';
font-size: 18px;
font-style: normal;
font-weight: 500;
line-height: 26px; /* 144.444% */
text-transform: capitalize;
	}
  </style>
  
  <svelte:window bind:innerWidth={viewpoortWidth} />
  
  <nav class="w-screen absolute top-0 left-0">
	<ContentWidth class="flex flex-row justify-between">
		<PrismicImage field={content.logo} class="w-auto h-10 lg:h-[52px] mt-12" />
	</ContentWidth>
  </nav>
  {#if viewpoortWidth>1024}
	  <ScreenWidthImage field={content.background_image} class="flex justify-between">
		<div class="w-2/3 flex flex-col justify-end items-start gap-12 pb-44">
			<img src={life} alt="life saving" class="h-20 xl:h-[165px]"/>
			<img src={devices} alt="devices" class="h-20 xl:h-[165px]"/>
			<img src={subtitle} alt="Protect Your Employees. Protect Your customers." class="mt-4"/>

		</div>
		<div class="flex flex-col justify-end items-end w-[30%] overflow-hidden">
			<div class="w-full flex flex-col items-center ">
				<PrismicImage field={content.aed} class="w-full -mb-36 z-10"/>
				<div class="bg-[#EA7724] text px-5 pt-48  pb-48 w-1/2 text">
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
	  <div class="w-screen relative pt-48 pb-24 overflow-hidden">
		<PrismicImage field={content.background_image} class="w-full h-full absolute top-1/2 -translate-y-1/2 left-1/2 -translate-x-1/2 object-cover" />
		<ContentWidth class="flex flex-col items-start justify-start">
			<img src={mobileLife} alt="life saving" class="h-[176px] mb-[16px]"/>
			<img src={mobileDevices} alt="devices" class="h-[84px] "/>
			<div class="subtitle mt-8">Protect Your Employees.</div>
			<div class="subtitle">Protect Your Customers.</div>
			<div class="flex flex-row relative flex-shrink-0 items-center">
				<div class="bg-[#EA7724] h-3/5 w-screen absolute top-[30%] left-[20%]"></div>
				<PrismicImage field={content.aed} class="w-3/4 mt-12 z-10 -translate-x-[20%] object-cover flex-shrink-0"/>
				<div class="text-mobile p-6 w-7/12 flex-shrink-0 -translate-x-1/2 translate-y-[15%]">AEDs and Program Management Currently Serving the Texas Hill Country and San Antonio area.</div>
			</div>
		</ContentWidth>
	  </div>
	  <footer class="w-screen bg-black pt-12 pb-16 relative">
		<ContentWidth class="h-full flex flex-col justify-center items-start gap-2">
			<div class="text-white">
				For information on an AED Program for Your Business or Organization:
			</div>
			<div class="text-white mt-4">
				Ryan Kohnen
			</div>
			<div class="text-white">
				210.273.7767
			</div>
			<div class="text-white">
				ryan@ryankohnen.com
			</div>
		</ContentWidth>
	  </footer>
  {/if}
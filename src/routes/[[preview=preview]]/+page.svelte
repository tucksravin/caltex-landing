<script lang='ts'>
  import ContentWidth from "$lib/components/ContentWidth/ContentWidth.svelte";
	import ScreenWidthImage from "$lib/components/ScreenWidth/ScreenWidthImage.svelte";
  import { PrismicImage } from "@prismicio/svelte";
  import life from "$lib/assets/icons/LifeSaving.svg"
  import devices from "$lib/assets/icons/Devices.svg"
  import subtitle from "$lib/assets/icons/subtitle.svg"
  import mobileLife from "$lib/assets/icons/m_LifeSaving.svg"
  import mobileDevices from "$lib/assets/icons/m_devices.svg"
  import DefaultButton from "$lib/components/Buttons/DefaultButton.svelte";
  import { fade, fly } from "svelte/transition";
  
	let { data } = $props();

	let viewpoortWidth=$state(1024)

	let isModalOpen = $state(false);

	$effect(()=>{
		isModalOpen;
		if (document.getElementsByTagName('body'))
			if(isModalOpen){
				(document.getElementsByTagName('body')[0] as HTMLElement).style.overflow = 'hidden';
			}else{
				(document.getElementsByTagName('body')[0] as HTMLElement).style.overflow = 'auto';
			}
			console.log('effect fired')
		}
	);
  
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
	<ContentWidth class="flex flex-row justify-between items-center h-36">
		<PrismicImage field={content.logo} class="w-auto h-10" />
		<DefaultButton onclick={()=>isModalOpen=true} >Request Info</DefaultButton>
	</ContentWidth>
  </nav>

  {#if isModalOpen}
  	<div class="w-screen h-screen fixed top-0 left-0 bg-black bg-opacity-80 backdrop-blur z-30 flex items-center justify-center" transition:fade>
	<button onclick={()=>isModalOpen=false} class="w-screen h-screen absolute top-0 left-0" aria-label="close"> </button>


	<ContentWidth class="blur-none bg-primary h-4/5 md:h-3/5 relative rounded-lg flex flex-col items-center justify-center text-center gap-16 px-9 md:px-16">
		<button class="absolute top-6 right-6 pointer-events-auto" onclick={()=>isModalOpen=false} aria-label="close">
			<i class="fa-sharp fa-solid fa-2xl fa-close"></i>
		</button>
		<h2 class="text-white"><span>Choosing our AED services&nbsp;</span><span> ensures your readiness&nbsp;</span><span> for emergencies.</span></h2>
		<h3 class="text-white">Contact Ryan Kohen at <span class="text-black">ryan@ryankohnen.com</span> <br/> or leave a message <span class="text-black">210.273.7767</span></h3>

	</ContentWidth>
	
	
	</div>
  {/if}

	<ScreenWidthImage field={content.background_image} class="flex justify-between" backdrop />
		
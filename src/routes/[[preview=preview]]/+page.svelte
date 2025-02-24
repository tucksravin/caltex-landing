<script lang='ts'>
  import ContentWidth from "$lib/components/ContentWidth/ContentWidth.svelte";
	import ScreenWidthImage from "$lib/components/ScreenWidth/ScreenWidthImage.svelte";
  import { PrismicImage, PrismicRichText } from "@prismicio/svelte";
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
		}
	);
  
	  const content = data.page.data
  </script>

  
  <svelte:window bind:innerWidth={viewpoortWidth} />
  
  <nav class="w-screen absolute top-0 left-0 z-20">
	<ContentWidth class="flex flex-row justify-between items-center h-36">
		<PrismicImage field={viewpoortWidth>768?content.logo:content.logo_mark} class="w-auto h-10" />
		<DefaultButton onclick={()=>isModalOpen=true} >Request Info</DefaultButton>
	</ContentWidth>
  </nav>

  {#if isModalOpen}
  	<div class="w-screen h-screen fixed top-0 left-0 bg-black bg-opacity-80 backdrop-blur z-30 flex items-center justify-center" transition:fade>
	<button onclick={()=>isModalOpen=false} class="w-screen h-screen absolute top-0 left-0" aria-label="close"> </button>


	<ContentWidth class="blur-none bg-primary h-4/5 md:h-3/5 relative rounded-lg flex flex-col items-center justify-center text-center gap-16 px-3 sm:px-9 md:px-16">
		<button class="absolute top-6 right-6 pointer-events-auto" onclick={()=>isModalOpen=false} aria-label="close">
			<i class="fa-sharp fa-solid fa-xl fa-close"></i>
		</button>
		<h2 class="text-white"><span>Choosing our AED services&nbsp;</span><span> ensures your readiness&nbsp;</span><span> for emergencies.</span></h2>
		<h3 class="text-white">Contact Ryan Kohen at <a href="mailto:ryan@ryankohnen.com" class="text-black">ryan@ryankohnen.com</a> <br/> or leave a message <a href="tel:210.273.7767" class="text-black">210.273.7767</a></h3>

	</ContentWidth>
	
	
	</div>
  {/if}

	<ScreenWidthImage field={content.background_image} class="flex justify-between" backdrop />
	<section id="s1" class="h-screen w-screen overflow-hidden">
		<ContentWidth class="flex flex-row h-full items-end relative">
			<PrismicImage class="md:w-2/3 mb-64" field={content.s1_title} />
			<div class="w-screen p-8 bg-primary text-dark absolute left-0 bottom-8 rounded-lg items-center flex">
				<h3 class="md:w-1/2 ">{content.s1_subtitle}</h3>
			</div>
			<PrismicImage class="absolute bottom-8 right-0 w-1/2 translate-x-[20%] hidden md:block" field={content.aed} />
			
		</ContentWidth>

	</section>
	<section id="s2" class="w-screen mt-20 lg:mt-52">
		<ContentWidth class="flex flex-col items-start justify-start gap-11 lg:gap-20">
			<h2 class="text-dark md:w-1/3">{content.s2_eyebrow}</h2>
			<div class="w-full flex justify-between flex-wrap">
				{#each content.s2_icons as icon, i}
				<div class="w-full md:w-1/2 pb-10 {i%2==0? "md:pr-5":"md:pl-5"}">
					<div class="h-40 md:h-52 w-full bg-dark text-primary flex flex-row justify-between items-center rounded-[7px] p-11 gap-11">
						<PrismicImage class="w-32" field={icon.icon} />
						<h3>{icon.label}</h3>
					</div>
				</div>
				{/each}
			</div>
			<div class=" md:w-1/3">
				<h3 class="text-dark">{content.s2_closing_text}</h3>
				<DefaultButton class="mt-11" onclick={()=>isModalOpen=true} >Request Info</DefaultButton>

			</div>
		</ContentWidth>
	</section>
	<section id="s3" class="w-screen mt-24 relative">
		<PrismicImage class="absolute h-[100vw] w-screen top-0 right-[4vw] lg:top-[5vw] lg:left-0 lg:h-[40vw] lg:w-[40vw] rounded-r-lg" field={content.s3_image}/>
		<ContentWidth class="h-full pt-[108vw] lg:py-[5vw] flex justify-end items-end text-dark relative">

			<div class="lg:w-1/2 h-full flex flex-col justify-between items-start lg:gap-10">
				<h2>{content.s3_title}</h2>
				<div class="flex flex-wrap gap-y-5 mt-12 lg:mt-0">
					{#each content.s3_bullets as bullet}
						<div class="w-full lg:w-1/2 h-12 flex lg:justify-between items-center pr-10">
							<svg xmlns="http://www.w3.org/2000/svg" class="h-7 w-7 mr-4" viewBox="0 0 22 22" fill="none">
								<path fill-rule="evenodd" clip-rule="evenodd" d="M14.6667 0H7.33333V7.33333L0 7.33333V14.6667H7.33333V22H14.6667V14.6667H22V7.33333L14.6667 7.33333V0Z" fill="#EA7724"/>
							</svg>
							<p>{bullet.text}</p>
						</div>
					{/each}
				</div>
				<div class="mt-12 lg:mt-0">
					<h3 class="text-dark">{content.s3_closing_text}</h3>
					<DefaultButton class="mt-6" onclick={()=>isModalOpen=true} >Request Info</DefaultButton>
				</div>
			</div>
		</ContentWidth>
	</section>
	<section id="s4" class="w-screen bg-primary text-white mt-10 lg:mt-24 py-24 relative overflow-hidden">
		<ContentWidth class="flex flex-col gap-10 lg:gap-20">
			<h2 class="lg:w-2/3">{content.s4_title}</h2>
			<div>
				<h3 class="lg:w-1/2">{content.s4_body}</h3>
				<DefaultButton class="mt-6" isWhite onclick={()=>isModalOpen=true} >Request Info</DefaultButton>
			</div>
			<div class="w-full flex justify-center flex-wrap text-white">
				{#each content.s4_image_blocks as block, i}
				<div class="w-full md:w-1/2 pb-10 {i%2==0? "md:pr-5":"md:pl-5"}">
					<div class="w-full aspect-[4/3] lg:aspect-video flex flex-col items-start justify-end gap-6 relative rounded-xl overflow-hidden p-6 md:p-12">
						<PrismicImage class="w-full h-full  absolute top-0 left-0 blur-sm brightness-75" field={block.image} />
						<h4 class="z-10 lg:w-1/2">{block.title}</h4>
						<p class="z-10">{block.body}</p>
					</div>
				</div>

				{/each}

			</div>
			<div class="w-screen h-52 p-12 bg-black text-white rounded-lg items-start flex gap-8 lg:mb-24">
				<svg class="w-6 sm:w-11" viewBox="0 0 44 39" fill="none" xmlns="http://www.w3.org/2000/svg">
					<path d="M17.125 1.74999H18.375V0.0862234L16.777 0.549411L17.125 1.74999ZM17.125 9L17.5379 10.1798L18.375 9.88685V9H17.125ZM9.5 20.125H8.25V21.375H9.5V20.125ZM17.125 20.125H18.375V18.875H17.125V20.125ZM17.125 37V38.25H18.375V37H17.125ZM1.5 37H0.25V38.25H1.5V37ZM42 1.74999H43.25V0.0862232L41.652 0.549412L42 1.74999ZM42 9L42.4129 10.1798L43.25 9.88685V9H42ZM34.375 20.125H33.125V21.375H34.375V20.125ZM42 20.125H43.25V18.875H42V20.125ZM42 37V38.25H43.25V37H42ZM26.375 37H25.125V38.25H26.375V37ZM15.875 1.74999V9H18.375V1.74999H15.875ZM16.7121 7.82017C13.9878 8.77367 11.8509 10.365 10.4027 12.5019C8.9579 14.6339 8.25 17.2326 8.25 20.125H10.75C10.75 17.6424 11.3546 15.5536 12.4723 13.9044C13.5866 12.26 15.2622 10.9763 17.5379 10.1798L16.7121 7.82017ZM9.5 21.375H17.125V18.875H9.5V21.375ZM15.875 20.125V37H18.375V20.125H15.875ZM17.125 35.75H1.5V38.25H17.125V35.75ZM2.75 37V20.125H0.25V37H2.75ZM2.75 20.125C2.75 11.3688 9.17761 5.35504 17.473 2.95058L16.777 0.549411C7.82239 3.14496 0.25 9.8812 0.25 20.125H2.75ZM40.75 1.74999V9H43.25V1.74999H40.75ZM41.5871 7.82017C38.8628 8.77367 36.7259 10.365 35.2777 12.5019C33.8329 14.6339 33.125 17.2326 33.125 20.125H35.625C35.625 17.6424 36.2296 15.5536 37.3473 13.9044C38.4616 12.26 40.1372 10.9763 42.4129 10.1798L41.5871 7.82017ZM34.375 21.375H42V18.875H34.375V21.375ZM40.75 20.125V37H43.25V20.125H40.75ZM42 35.75H26.375V38.25H42V35.75ZM27.625 37V20.125H25.125V37H27.625ZM27.625 20.125C27.625 11.3688 34.0526 5.35504 42.348 2.95058L41.652 0.549412C32.6974 3.14496 25.125 9.8812 25.125 20.125H27.625Z" fill="#EA7724"/>
				</svg>
				<div class="w-4/5 xl:w-3/5 xxl:w-1/2 h-full items-start justify-center flex flex-col gap-3">
					<h3>{content.s4_quote}</h3>
					<p>{content.s4_attribution}</p>
				</div>
					
			</div>


		</ContentWidth>
	</section>
	<section id="s5">
		<ScreenWidthImage field={content.s5_background} class="h-full flex flex-col items-start justify-end py-24" darken>
			<PrismicImage class="w-3/5" field={content.s5_title} />
			<DefaultButton class="mt-12" isWhite onclick={()=>isModalOpen=true} >Request Info</DefaultButton>
			
		</ScreenWidthImage>

	</section>

	<section id="s6" class="w-screen mt-20 lg:mt-52 text-dark">
		<ContentWidth>
			<div class="w-full flex flex-row flex-wrap gap-y-10">
				<div class="w-full md:w-1/2 flex flex-col gap-10 md:pr-5">
					<h2>{content.s6_title}</h2>
					<div>
						<h3>{content.s6_body}</h3>
						<DefaultButton class="mt-6" onclick={()=>isModalOpen=true}>Request Info</DefaultButton>
					</div>
				</div>
				<div class="w-full md:w-1/2 flex flex-col gap-10 md:pl-5">
					{#each content.s6_steps as step }
					<div class="p-4 md:p-8 pl-4 md:pl-0 h-48 flex justify-start gap-4 bg-black text-white rounded-lg">
						<div class="w-1/3 xl:w-1/4 h-full flex justify-center items-center md:items-start">
							<PrismicImage field={step.number} class="h-3/5 md:h-4/5 xl:h-full" />
						</div>
						<div class="w-2/3 xl:w-3/4 h-full flex flex-col items-start justify-center md:justify-start md:-translate-x-[5%]">
							<h3>{step.title}</h3>
							<p class="mt-4">{step.body}</p>
						</div>

					</div>
						
					{/each}
				</div>
			</div>
			<div>

			</div>
		</ContentWidth>
	</section>
	<section id="s7" class="w-screen mt-24 lg:mt-52 relative">
		<PrismicImage class="absolute h-[100vw] w-screen top-0 right-[4vw] lg:top-[5vw] lg:left-0 lg:h-[40vw] lg:w-[40vw] rounded-r-lg" field={content.s7_image}/>
		<ContentWidth class="h-full pt-[108vw] lg:py-[5vw] flex justify-end items-end text-dark relative">

			<div class="lg:w-1/2 h-full flex flex-col justify-between items-start lg:gap-10">
				<h2>{content.s7_title}</h2>
				<div class="flex flex-col gap-y-5 mt-12 lg:mt-0">
					
					<div class="rich-text">
						<PrismicRichText field={content.s7_body} />
					</div>
				</div>
				<div class="mt-12 lg:mt-0">
					<DefaultButton  onclick={()=>isModalOpen=true} >Request Info</DefaultButton>
				</div>
			</div>
		</ContentWidth>
	</section>

	<section id="s8" class="w-screen bg-primary text-white mt-10 md:mt-48 py-10 md:py-24 relative">
		<ContentWidth class="flex flex-col md:flex-row">
			<div class="w-full md:w-1/2 flex flex-col items-center md:items-start md:pr-5">
				<PrismicImage class="w-full" field={content.s8_title} />
				<PrismicImage class="w-2/3 md:-translate-x-[20%]" field={content.s8_aed} />
			</div>
			<div class="w-full md:w-1/2 flex flex-col md:pl-5">
				<div class="rich-text text-dark mt-4">
					<PrismicRichText field={content.s8_dark_text} />
				</div>
				<div class="rich-text text-white">
					<PrismicRichText field={content.s8_light_text} />
				</div>
			</div>
		</ContentWidth>
	</section>
	<footer class="lg:h-32 w-screen bg-light">
		
		<ContentWidth class="flex flex-col lg:flex-row lg:justify-between h-full text-dark lg:items-center gap-8 py-8">
			<PrismicImage field={viewpoortWidth>768?content.logo:content.logo_mark} class="-ml-3 h-10" />
			<div class="flex flex-col lg:flex-row gap-8 opacity-60">
				<a href="mailto:ryan@ryankohnen.com">ryan@ryankohnen.com</a>
				<a href="tel:210.273.7767">210.273.7767</a>
			</div>
			<div class="opacity-60">
				<span>{"©"+ new Date().getFullYear().toString() + " Caltex Medical"}</span>
			</div>
		</ContentWidth>
	</footer>
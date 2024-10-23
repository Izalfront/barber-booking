<script lang="ts">
	import BarberScreenLoading from '$lib/images/components/BarberScreenLoading.svelte';

	import onboard1 from './Onboarding/img/onboard1.png';
	import onboard2 from './Onboarding/img/onboard2.png';
	import onboard3 from './Onboarding/img/onboard3.png';
	// svelte-ignore non_reactive_update
	let currentSlide = 0;
	const slides = [
		{
			id: 1,
			title: 'Welcome Gobars',
			description: `Find the best grooming experience in your city with just one tap! Don't miss out on the haircut or treatment of your dreams. Let's start now!`,
			image: onboard1
		},
		{
			id: 2,
			title: 'Loooking for barber?',
			description:
				'Find the best barbershop around you in seconds, make an appointment, and enjoy the best grooming experience..',
			image: onboard2
		},
		{
			id: 3,
			title: 'Everything in your hands',
			description:
				'With Gobar, find high-quality barbershops, see reviews, and make appointments easily. Achieve your confident appearance!',
			image: onboard3
		}
	];

	function nextSlide() {
		if (currentSlide < slides.length - 1) {
			currentSlide++;
		} else {
			window.location.href = '/Login';
		}
	}

	function getStarted() {
		window.location.href = '/Login';
	}

	function undoSlide() {
		if (currentSlide > 0) {
			currentSlide--;
		}
	}

	let loading = true;

	// Simulasi loading
	import { onMount } from 'svelte';
	function appOnLoad() {
		setTimeout(() => {
			loading = false;
		}, 1500);
	}

	onMount(() => {
		if (document.readyState === 'complete') {
			appOnLoad();
		} else {
			document.onreadystatechange = () => {
				if (document.readyState === 'complete') {
					appOnLoad();
				}
			};
		}
	});
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<div class="w-full max-w-[500px] mx-auto text-base overflow-x-hidden h-screen">
	<BarberScreenLoading {loading} />
	<main class="h-screen bg-gray-200 overflow-y-hidden">
		<img src={slides[currentSlide].image} alt="" class="z-10" />
		<div class="w-full bg-[#F99417] z-20 pt-6 rounded-t-3xl -translate-y-14 h-full">
			<div class="text-start mx-4">
				<h2 class="text-white font-semibold text-2xl">{slides[currentSlide].title}</h2>
				<p class="text-white font-light text-lg leading-tight mt-2">
					{slides[currentSlide].description}
				</p>
			</div>
			<br />
			<div class="text-center">
				<button class="bg-[#363062] px-6 py-2 text-white" onclick={nextSlide}>
					{#if currentSlide < slides.length - 1}
						Next
					{:else}
						Go to Login
					{/if}
				</button>
				<button onclick={undoSlide} class="bg-[#363062] px-6 py-2 text-white">Undo</button>
			</div>
			<div class="text-center mt-2">
				<button onclick={getStarted} class="bg-[#363062] py-3 text-white w-[40vh] rounded-lg"
					>Get Started</button
				>
			</div>
		</div>
	</main>
</div>

<script lang="ts">
	import pattern from './img/pattern.png';
	import master from './img/masterpc.png';
	import { goto } from '$app/navigation';
	import Rating from '../../../find-barber/rating/Rating.svelte';
	import Tags from './Tags.svelte';

	let tags = [
		{ text: 'Overall good', highlighted: true, active: true },
		{ text: 'Good service', highlighted: true },
		{ text: 'Satisfying' },
		{ text: 'Comfortable' },
		{ text: 'Recommended' },
		{ text: 'Cheap' },
		{ text: 'Perfect results' },
		{ text: 'Accurate estimate' }
	];

	function goToDetailBarber() {
		goto('/appointment');
	}

	function goToInvoice() {
		goto('/appointment/detail-appointment/invoice');
	}
</script>

<div class="w-full max-w-[450px] mx-auto text-base h-screen bg-[#363062] overflow-y-auto">
	<!-- Header - Fixed at top -->
	<!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
	<div class="sticky top-0 bg-[#363062] px-6 py-1 z-20">
		<!-- svelte-ignore a11y_click_events_have_key_events -->
		<h1
			on:click={goToDetailBarber}
			class="text-xl font-semibold my-6 flex gap-x-4 items-center text-white cursor-pointer"
		>
			<svg
				width="18"
				height="14"
				viewBox="0 0 18 14"
				fill="none"
				xmlns="http://www.w3.org/2000/svg"
			>
				<path
					d="M17 7H1M1 7L7 1M1 7L7 13"
					stroke="#fff"
					stroke-width="2"
					stroke-linecap="round"
					stroke-linejoin="round"
				/>
			</svg>
			Rating & review
		</h1>
	</div>

	<!-- Main Content -->
	<div class="relative min-h-[calc(100vh-116px)]">
		<!-- Background pattern -->
		<img class="w-full h-48 object-cover" src={pattern} alt="Pattern background" />

		<!-- Top Card -->
		<div class="absolute top-4 left-4 right-4 bg-white/20 rounded-lg shadow-lg p-4">
			<div class="flex items-center gap-4">
				<div class="w-24 h-24 flex-shrink-0 overflow-hidden rounded-lg">
					<img class="w-full h-full object-cover" src={master} alt="Masterimage" />
				</div>

				<div class="text-white">
					<h1 class="font-semibold text-lg">Master piece Barbershop - Haircut styling</h1>
					<div class="flex flex-col text-sm mt-2">
						<p>Jogja Expo Centre (2 km)</p>
						<p>5.0 (24)</p>
					</div>
				</div>
			</div>
		</div>

		<!-- Bottom Card -->
		<div
			class="absolute top-48 left-0 right-0 bg-white rounded-t-3xl p-6 min-h-[calc(100vh-192px)]"
		>
			<!-- Date & Time -->
			<div class="flex justify-start scale-125 ml-12">
				<Rating />
			</div>
			<div class="mt-12 ml-1">
				<p class="text-lg">Review</p>
			</div>
			<div class="mt-6">
				<Tags {tags} />
			</div>
			<div class="w-full">
				<button
					class="w-full h-14 rounded-xl text-white font-semibold bg-[#363062] mt-4 tracking-wide py-4 flex items-center justify-center gap-x-4 translate-y-36"
					>Send</button
				>
			</div>
		</div>
	</div>
</div>

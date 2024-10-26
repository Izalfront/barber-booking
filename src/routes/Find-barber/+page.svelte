<script lang="ts">
	import ListBarberLocation from './list-barber-location/ListBarberLocation.svelte';

	function goToHome() {
		window.location.href = './home';
	}
</script>

<div>
	<!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
	<div class="bg-white px-6 py-3">
		<!-- svelte-ignore a11y_click_events_have_key_events -->
		<h1 on:click={goToHome} class="text-xl font-semibold mt-8 mb-1 flex gap-x-4 items-center">
			<svg
				width="18"
				height="14"
				viewBox="0 0 18 14"
				fill="none"
				xmlns="http://www.w3.org/2000/svg"
			>
				<path
					d="M17 7H1M1 7L7 1M1 7L7 13"
					stroke="#111827"
					stroke-width="2"
					stroke-linecap="round"
					stroke-linejoin="round"
				/>
			</svg>Find a barber nearby
		</h1>
	</div>
	<div>
		<!-- svelte-ignore a11y_missing_attribute -->
		<iframe
			class="w-[25rem] mx-auto rounded-2xl"
			src="https://www.google.com/maps/embed?pb=!1m16!1m12!1m3!1d7966.1719261473!2d114.6040461645056!3d-3.3289382166469!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!2m1!1sgoogle%20maps%20barbershop%20banjarmasin%20buka%20sekarang!5e0!3m2!1sid!2sid!4v1729906363476!5m2!1sid!2sid"
			width="600"
			height="450"
			style="border:0;"
			loading="lazy"
			referrerpolicy="no-referrer-when-downgrade"
		></iframe>
	</div>
	<div class="px-6">
		<ListBarberLocation />
	</div>
</div>

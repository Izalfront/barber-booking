<script lang="ts">
	import Date from './Date.svelte';

	function goToDetailBarber() {
		window.location.href = './detail-barber';
	}
</script>

<div class="w-full max-w-[450px] mx-auto text-base overflow-x-hidden h-screen">
	<div class="p-6">
		<!-- svelte-ignore a11y_click_events_have_key_events -->
		<!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
		<h1 on:click={goToDetailBarber} class="text-xl font-semibold my-6 flex gap-x-4 items-center">
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
			</svg>Book Appointmnet
		</h1>
		<div>
			<Date />
		</div>
	</div>
</div>

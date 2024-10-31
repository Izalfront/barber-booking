<script lang="ts">
	import AvaibleTime from './AvaibleTime.svelte';
	import ChoiceService from './ChoiceService.svelte';
	import Date from './Date.svelte';
	import Payment from './Payment.svelte';
	import calendar from './img/calendar-mark.svg';
	import { goto } from '$app/navigation';

	function goToPayNow() {
		goto('/appointment/detail-appointment');
	}

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
		<div>
			<ChoiceService />
		</div>
		<div>
			<AvaibleTime />
		</div>
		<div>
			<Payment />
		</div>
		<div>
			<button
				on:click={goToPayNow}
				class="w-full h-14 rounded-xl text-white font-semibold bg-[#363062] mt-4 tracking-wide flex items-center justify-center gap-2"
				>Deal booking <img src={calendar} alt="" /></button
			>
		</div>
	</div>
</div>

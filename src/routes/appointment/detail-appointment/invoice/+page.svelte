<script lang="ts">
	import pattern from '../../img/pattern.png';
	import message from '../../img/message.png';
	import completed from '../../img/completed.png';
	import { goto } from '$app/navigation';
	import TotalPayment from './TotalPayment.svelte';
	import download from '../../img/download.svg';

	function goToDetailBarber() {
		goto('/appointment');
	}

	function goToInvoice() {
		goto('/appointment/detail-appointment');
	}

	function popUpDownload() {
		alert('Completed');
	}
</script>

<div class="w-full max-w-[450px] mx-auto text-base h-screen bg-[#363062] overflow-y-hidden">
	<!-- Header - Fixed at top -->
	<!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
	<div class="sticky top-0 bg-[#363062] p-6 z-20">
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
			Your Appointment
		</h1>
	</div>

	<!-- Main Content -->
	<div class="relative min-h-[calc(100vh-116px)]">
		<!-- Background pattern -->
		<img class="w-full h-full object-cover" src={pattern} alt="Pattern background" />

		<!-- Top Card -->
		<div class="absolute top-[2rem] left-[9.5rem]">
			<div class="flex items-center gap-4">
				<div class="w-auto h-32 flex-shrink-0 overflow-hidden rounded-lg">
					<img class="w-full h-full object-cover" src={completed} alt="Masterimage" />
				</div>
			</div>
		</div>
		<div class="absolute top-[10rem]">
			<div class="flex flex-col justify-center items-center text-center text-white mt-6">
				<h1 class="text-lg font-semibold">Booking Succesfully</h1>
				<p class="font-light mx-16">Immediately check the booking menu for detailed information</p>
			</div>
		</div>
		<!-- Bottom Card -->
		<div
			class="absolute top-80 left-0 right-0 bg-white rounded-t-3xl p-6 min-h-[calc(100vh-192px)]"
		>
			<!-- Date & Time -->
			<div class="flex flex-col">
				<div class="flex gap-3 items-center">
					<h1 class="font-semibold text-lg">Master piece Barbershop - Haircut styling</h1>
				</div>
				<div class="mt-2">
					<p class="text-lg text-slate-500 font-medium">Basic haircut , Message</p>
				</div>
				<div class="mt-2">
					<p class=" text-slate-500">Sun, 15 Jan</p>
				</div>
			</div>

			<!-- Service List -->
			<div class="mt-6">
				<TotalPayment />
				<div class="flex gap-4 mt-6">
					<button
						on:click={goToInvoice}
						class="w-full h-14 rounded-xl text-white font-semibold bg-[#363062] mt-4 tracking-wide flex items-center justify-center gap-2"
						>Back</button
					>
					<button
						on:click={popUpDownload}
						class="w-full h-14 rounded-xl text-[#363062] font-semibold border-2 border-[#363062] mt-4 tracking-wide flex items-center justify-center gap-2"
						>Download <img src={download} alt="" /></button
					>
				</div>
			</div>
		</div>
	</div>
</div>

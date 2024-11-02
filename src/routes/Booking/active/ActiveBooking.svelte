<script lang="ts">
	import finished from '../img/finished.svg';
	import stopwatch from '../img/stopwatch.svg';
	import cut from '../img/Scissors.svg';
	import schedule from '../img/schedule.svg';
	import ProgressTracker from './ProgressTracker.svelte';
	import master from '../../home/img/barber3.png';
	import pinned from '../img/locationhistory.svg';
	import rating from '../../home/img/rating.svg';
	import googleMaps from '../../detail-barber/img/logos_google-maps.svg';
	import chat from '../img/chat.svg';
	import calendar from '../img/calendar-fill.svg';
	import List from './List.svelte';
	import timer from '../img/stopwatch.svg';

	let currentStep = 1;

	function goToStepWaiting() {
		if (currentStep < 4) {
			currentStep++;
		}
	}

	function getStatusText(step: number) {
		switch (step) {
			case 1:
				return { title: 'Time Estimation', time: '- 50 Menit' };
			case 2:
				return { title: 'On Process', time: '30 Menit' };
			case 3:
				return { title: 'Finished', time: 'Yeay!' };
			default:
				return { title: 'Time Estimation', time: '- 50 Menit' };
		}
	}
</script>

<div>
	<div class="flex justify-between gap-3 mt-3 mx-[1.6rem]">
		<!-- svelte-ignore a11y_click_events_have_key_events -->
		<!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
		<img
			class="w-6 h-auto cursor-pointer"
			src={schedule}
			alt=""
			on:click={() => (currentStep = 1)}
		/>
		<!-- svelte-ignore a11y_click_events_have_key_events -->
		<!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
		<img
			class="w-6 h-auto cursor-pointer"
			src={stopwatch}
			alt=""
			on:click={() => (currentStep = 2)}
		/>
		<!-- svelte-ignore a11y_click_events_have_key_events -->
		<!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
		<img class="w-6 h-auto cursor-pointer" src={cut} alt="" on:click={() => (currentStep = 3)} />
		<!-- svelte-ignore a11y_click_events_have_key_events -->
		<!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
		<img
			class="w-6 h-auto cursor-pointer"
			src={finished}
			alt=""
			on:click={() => (currentStep = 4)}
		/>
	</div>

	<div class="mt-6">
		<ProgressTracker {currentStep} />
	</div>

	<div class="mt-6">
		<div class="bg-white p-4 shadow-lg rounded-xl">
			<div class="flex">
				<img class="w-auto h-24 mr-3" src={master} alt="" />
				<div>
					<h1 class="font-semibold text-lg">Master piece</h1>
					<p class="text-slate-500 text-sm flex gap-2">
						<img src={pinned} alt="" /> Jogja Expo Centre (2 km)
					</p>
					<p class="text-slate-500 text-sm flex gap-2">
						<img src={rating} alt="" /> 5.0 (24)
					</p>
				</div>
			</div>
			<div class="mt-4 border-t">
				<div class="flex justify-between mt-4">
					<div class="flex gap-6 w-auto">
						<div class="flex flex-col items-center">
							<img class="w-7 h-7" src={googleMaps} alt="" />
							<p>Maps</p>
						</div>
						<div class="flex flex-col items-center">
							<img class="w-7 h-7" src={chat} alt="" />
							<p>Chat</p>
						</div>
					</div>
					<button class="bg-[#363062] rounded-lg font-medium px-6 text-white tracking-wide">
						Cancel
					</button>
				</div>
			</div>
		</div>
	</div>

	{#if currentStep <= 3}
		<div class="flex justify-between bg-[#EDEFFB] p-4 rounded-lg mt-4">
			<div class="flex items-center gap-2">
				<img src={timer} alt="timer" />
				<h1 class="font-semibold text-lg">{getStatusText(currentStep).title}</h1>
			</div>
			<h1 class="font-semibold text-lg">{getStatusText(currentStep).time}</h1>
		</div>
	{/if}

	<div>
		<div class="flex gap-2 mt-6">
			<img src={calendar} alt="" />
			<p class="font-semibold text-lg">Date & time</p>
		</div>
		<p class="text-slate-500 tracking-wide font-medium">Sun, 15 Jan - 08:00 AM</p>
	</div>

	<div class="mt-5">
		<List />
	</div>
</div>

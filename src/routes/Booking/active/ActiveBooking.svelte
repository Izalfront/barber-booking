<script lang="ts">
	import finished from '../img/finished.svg';
	import stopwatch from '../img/stopwatch.svg';
	import cut from '../img/Scissors.svg';
	import schedule from '../img/schedule.svg';
	import ProgressTracker from './ProgressTracker.svelte';
	import master from '../../home/img/barber3.png';
	import pinned from '../img/locationhistory.svg';
	import rating from '../../home/img/rating.svg';

	let currentStep = 1;
</script>

<div>
	<div class="flex justify-between gap-3 mt-3">
		<img class="w-6 h-auto" src={schedule} alt="" />
		<img class="w-6 h-auto" src={stopwatch} alt="" />
		<img class="w-6 h-auto" src={cut} alt="" />
		<img class="w-6 h-auto" src={finished} alt="" />
	</div>
	<div class="mt-6">
		<ProgressTracker {currentStep} />
	</div>
	<div class="mt-6">
		<div class=" bg-white p-4 border rounded-lg">
			<div class="flex">
				<img class="w-auto h-24 mr-3" src={master} alt="" />
				<div>
					<h1 class="font-semibold text-lg">Master piece</h1>
					<p class="text-slate-500 text-sm flex gap-2">
						<img src={pinned} alt="" /> Jogja Expo Centre (2 km)
					</p>
					<p class="text-slate-500 text-sm flex gap-2"><img src={rating} alt="" /> 5.0 (24)</p>
				</div>
			</div>
			<div class="mt-4 border-t">
				<div class="mt-4">
					<div></div>
					<button class="bg-[#363062] rounded-lg font-medium py-2 px-6 text-white tracking-wide"
						>Cancel</button
					>
				</div>
			</div>
		</div>
	</div>
</div>

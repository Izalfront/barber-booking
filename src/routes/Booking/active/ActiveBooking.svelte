<script lang="ts">
	import finished from '../img/finished.svg';
	import stopwatch from '../img/stopwatch.svg';
	import cut from '../img/Scissors.svg';
	import schedule from '../img/schedule.svg';
	import ProgressTracker from './ProgressTracker.svelte';

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
</div>

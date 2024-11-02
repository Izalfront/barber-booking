<script lang="ts">
	interface Step {
		id: string;
		label: string;
	}

	export let currentStep: number = 1;
	export let steps: Step[] = [
		{ id: 'booked', label: 'Booked' },
		{ id: 'waiting', label: 'Waiting' },
		{ id: 'process', label: 'On Process' },
		{ id: 'finished', label: 'Finished' }
	];

	let progressWidth: string;
	$: progressWidth = `${(100 * Math.max(0, currentStep - 1)) / (steps.length - 1)}%`;

	const isActive = (index: number): boolean => index + 1 <= currentStep;
	const isCompleted = (index: number): boolean => index + 1 < currentStep;
</script>

<div class="w-full max-w-xl mx-auto">
	<div class="relative">
		<!-- Progress Line -->
		<div class="absolute top-[12%] left-0 right-0 h-2 bg-gray-200 rounded-full"></div>
		<div
			class="absolute top-[12%] left-0 h-2 bg-[#F99417] transition-all duration-500 rounded-full"
			style="width: {progressWidth}"
		></div>

		<div class="relative flex justify-between">
			{#each steps as step, index}
				<div class="flex flex-col items-center">
					<div
						class="w-6 h-6 rounded-full border-[4px] flex items-center justify-center transition-all duration-300"
						class:border-[#363062]={isActive(index)}
						class:bg-[#363062]={isActive(index)}
						class:text-white={isActive(index)}
						class:border-gray-300={!isActive(index)}
						class:bg-white={!isActive(index)}
						class:text-gray-500={!isActive(index)}
					></div>
					<!-- Label -->
					<span
						class="mt-2 font-medium transition-colors duration-300 bg-[#363062] rounded-full py-1 px-2"
						class:text-white={isActive(index)}
						class:text-[#ffff]={!isActive(index)}
					>
						{step.label}
					</span>
				</div>
			{/each}
		</div>
	</div>
</div>

<script lang="ts">
	interface Step {
		id: string;
		label: string;
		icon: string;
	}

	export let currentStep = 0;
	export let steps: Step[] = [
		{ id: 'booked', label: 'Booked', icon: 'schedule' },
		{ id: 'waiting', label: 'Waiting', icon: 'stopwatch' },
		{ id: 'process', label: 'On Process', icon: 'cut' },
		{ id: 'finished', label: 'Finished', icon: 'finished' }
	];

	$: progressWidth = `${(100 * Math.max(0, currentStep)) / (steps.length - 1)}%`;

	const isActive = (index: number) => index <= currentStep;
	const isCompleted = (index: number) => index < currentStep;

	const isActiveLabel = (index: number) => currentStep;
</script>

<div class="w-full max-w-xl mx-auto">
	<div class="relative">
		<!-- Progress Line -->
		<!-- svelte-ignore element_invalid_self_closing_tag -->
		<div class="absolute top-[16%] left-0 right-0 h-2 bg-gray-200 -translate-y-1/2 rounded-full" />
		<!-- svelte-ignore element_invalid_self_closing_tag -->
		<div
			class="absolute top-[16%] left-0 h-2 bg-[#F99417] -translate-y-1/2 transition-all duration-500 rounded-full"
			style="width: {progressWidth}"
		/>

		<div class="relative flex justify-between">
			{#each steps as step, index}
				<div class="flex flex-col items-center">
					<!-- Circle with Icon -->
					<div
						class="w-6 h-6 rounded-full border-[4px] flex items-center justify-center transition-all duration-300"
						class:border-[#363062]={isActive(index)}
						class:bg-[#fff]={isActive(index)}
						class:text-white={isActive(index)}
						class:border-gray-300={!isActive(index)}
						class:bg-white={!isActive(index)}
						class:text-gray-500={!isActive(index)}
					>
						{#if isCompleted(index)}
							<!-- <svg class="w-4 h-4" viewBox="0 0 24 24" fill="none" stroke="currentColor">
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M5 13l4 4L19 7"
								/>
							</svg> -->
						{:else}
							<!-- <img class="w-4 h-4" src={`../img/${step.icon}.svg`} alt={step.label} /> -->
						{/if}
					</div>
					<!-- Label -->
					<span
						class="mt-2 font-medium transition-colors duration-300 bg-[#363062] rounded-full py-1 px-2"
						class:text-white={isActiveLabel(index)}
					>
						{step.label}
					</span>
				</div>
			{/each}
		</div>
	</div>
</div>

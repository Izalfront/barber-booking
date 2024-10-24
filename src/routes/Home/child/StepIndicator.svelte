<script lang="ts">
	export let totalSteps: number = 5;
	export let currentStep: number = 4;
	export let onStepClick: ((step: number) => void) | undefined = undefined;

	$: steps = Array.from({ length: totalSteps }, (_, i) => i + 1);

	function handleClick(step: number) {
		if (onStepClick) {
			onStepClick(step);
		}
	}
</script>

<div class="flex items-center gap-2">
	{#each steps as step}
		<!-- svelte-ignore element_invalid_self_closing_tag -->
		<button
			on:click={() => handleClick(step)}
			class={`h-2 rounded-full transition-all duration-300 cursor-pointer
          ${step === currentStep ? 'w-8 bg-indigo-900' : 'w-2 bg-gray-200 hover:bg-gray-300'}`}
			aria-label={`Go to step ${step} of ${totalSteps}`}
			aria-current={step === currentStep ? 'step' : undefined}
		/>
	{/each}
</div>

<script lang="ts">
	import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();
	let activeTab = 'about';

	const features = [
		{ id: 'about', label: 'About' },
		{ id: 'review', label: 'Review' },
		{ id: 'schedule', label: 'Schedule' },
		{ id: 'service', label: 'Service' }
	];

	function handleTabClick(feature: string) {
		activeTab = feature;
		dispatch('change', feature);
	}
</script>

<div class="flex justify-around">
	{#each features as feature}
		<button
			class="px-4 py-2 {activeTab === feature.id
				? 'text-[#363062] font-semibold border-b-2 border-[#363062]'
				: 'text-gray-500'}"
			on:click={() => handleTabClick(feature.id)}
		>
			{feature.label}
		</button>
	{/each}
</div>

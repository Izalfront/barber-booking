<script lang="ts">
	let data = [
		{
			id: 'all_service',
			name: 'All Service'
		},
		{
			id: 'basic_haircut',
			name: 'Basic haircut'
		},
		{
			id: 'coloring',
			name: 'Coloring'
		},
		{
			id: 'treatment',
			name: 'Treatment'
		}
	];

	let activeFilter = 'all_service';

	function handleClickFilter(tabName: string) {
		activeFilter = tabName;
	}
</script>

<div class="flex gap-x-4 overflow-x-scroll no-scrollbar">
	{#each data as filter}
		<button
			onclick={() => handleClickFilter(filter.id)}
			class={`${activeFilter == filter.id ? 'bg-gray-200 p-2 rounded-lg border border-black whitespace-nowrap' : 'bg-gray-50 p-2 rounded-lg border whitespace-nowrap'}`}
			>{filter.name}</button
		>
	{/each}
</div>

<style>
	.no-scrollbar::-webkit-scrollbar {
		display: none;
	}

	.no-scrollbar {
		-ms-overflow-style: none;
		scrollbar-width: none;
	}

	.active {
		background-color: #edeffb;
		padding: 2;
	}

	.active-text {
		color: #363062;
		font-weight: 600;
	}
</style>

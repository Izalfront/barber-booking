<script lang="ts">
	let avaibleTime = [
		{ time: '08.00', active: false },
		{ time: '09.00', active: false },
		{ time: '10.00', active: false },
		{ time: '11.00', active: false },
		{ time: '12.00', active: false },
		{ time: '13.00', active: false }
	];

	function activedTimes(index: number) {
		avaibleTime = avaibleTime.map((item, i) => ({
			...item,
			active: i === index
		}));
	}
</script>

<div class="mt-6 mb-3">
	<h1 class="font-semibold text-lg leading-tight my-2">Available time</h1>
	<div class="grid grid-cols-4 gap-4">
		{#each avaibleTime as data, index}
			<!-- svelte-ignore a11y_click_events_have_key_events -->
			<!-- svelte-ignore a11y_no_static_element_interactions -->
			<div
				on:click={() => activedTimes(index)}
				class="px-4 py-2 rounded-lg border-2"
				class:bg-gray-100={data.active}
			>
				<p>{data.time}</p>
			</div>
		{/each}
	</div>
</div>

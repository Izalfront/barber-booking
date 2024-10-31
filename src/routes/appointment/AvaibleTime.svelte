<script lang="ts">
	let avaibleTime = [
		{
			time: '08.00'
		},
		{
			time: '08.00'
		},
		{
			time: '08.00'
		},
		{
			time: '08.00'
		},
		{
			time: '08.00'
		},
		{
			time: '08.00'
		}
	];
</script>

<div class="mt-6 mb-3">
	<h1 class="font-semibold text-lg leading-tight my-2">Available time</h1>
	<div class="grid grid-cols-4 gap-4">
		{#each avaibleTime as data}
			<div class="px-4 py-2 rounded-lg border-2">
				<p>{data.time}</p>
			</div>
		{/each}
	</div>
</div>

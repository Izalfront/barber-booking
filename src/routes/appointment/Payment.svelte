<script lang="ts">
	let totalPayment = [
		{ title: 'Basic haircut', salary: 20 },
		{ title: 'Hair coloring', salary: 30 },
		{ title: 'Hair coloring', salary: 30 }
	];

	let total = totalPayment.reduce((acc, item) => acc + item.salary, 0);
</script>

<div>
	<h1 class="font-semibold text-lg leading-tight my-2">Payment summary</h1>

	{#each totalPayment as data}
		<div class="flex justify-between my-2">
			<div>
				<p class="text-lg">{data.title}</p>
			</div>
			<div>
				<p class="font-medium text-lg">${data.salary}</p>
			</div>
		</div>
	{/each}

	<div class="border-t my-3"></div>

	<div class="flex justify-between">
		<div>
			<p class="text-lg font-semibold">Total Payment</p>
		</div>
		<div>
			<p class="font-semibold text-lg">${total}</p>
		</div>
	</div>
</div>

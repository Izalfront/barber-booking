<script lang="ts">
	// Constants for min/max values
	const MIN_DISTANCE = 0.1;
	const MAX_DISTANCE = 100;

	// Reactive variables
	let nearest = 0.1;
	let farthest = 10;

	// Validate and update nearest value
	function updateNearest(value: string | number) {
		let newValue = typeof value === 'string' ? parseFloat(value) : value;

		// Handle invalid inputs
		if (isNaN(newValue)) {
			newValue = MIN_DISTANCE;
		}

		// Clamp values
		newValue = Math.max(MIN_DISTANCE, Math.min(newValue, MAX_DISTANCE));
		newValue = Math.min(newValue, farthest);

		nearest = Number(newValue.toFixed(1));
	}

	// Validate and update farthest value
	function updateFarthest(value: string | number) {
		let newValue = typeof value === 'string' ? parseFloat(value) : value;

		// Handle invalid inputs
		if (isNaN(newValue)) {
			newValue = nearest;
		}

		// Clamp values
		newValue = Math.max(nearest, Math.min(newValue, MAX_DISTANCE));

		farthest = Number(newValue.toFixed(1));
	}

	// Calculate slider position percentage
	function calculatePosition(value: number): number {
		return (value / MAX_DISTANCE) * 100;
	}

	// Format number for display
	function formatNumber(num: number): string {
		return num.toFixed(1);
	}
</script>

<div class="w-full max-w-2xl mx-auto">
	<h1 class="text-xl font-semibold text-black mb-3">Distance</h1>
	<div class="bg-white rounded-lg shadow-sm p-4">
		<div class="flex items-center justify-between gap-4 mb-2">
			<div class="flex-1">
				<label for="nearest" class="block text-sm text-gray-600 mb-1">Nearest</label>
				<div class="relative">
					<input
						type="number"
						id="nearest"
						value={nearest}
						on:input={(e) => updateNearest(e.currentTarget.value)}
						min={MIN_DISTANCE}
						max={farthest}
						step="0.1"
						class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 appearance-none pr-12"
					/>
					<span class="absolute right-3 top-1/2 -translate-y-1/2 text-gray-500">km</span>
				</div>
			</div>

			<div class="flex items-center justify-center h-full pt-6">
				<div class="w-8 h-[2px] bg-gray-300"></div>
			</div>

			<div class="flex-1">
				<label for="farthest" class="block text-sm text-gray-600 mb-1">Farthest</label>
				<div class="relative">
					<input
						type="number"
						id="farthest"
						value={farthest}
						on:input={(e) => updateFarthest(e.currentTarget.value)}
						min={nearest}
						max={MAX_DISTANCE}
						step="0.1"
						class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 appearance-none pr-12"
					/>
					<span class="absolute right-3 top-1/2 -translate-y-1/2 text-gray-500">km</span>
				</div>
			</div>
		</div>

		<div class="relative w-full h-2 bg-gray-200 rounded-full mt-6">
			<!-- svelte-ignore element_invalid_self_closing_tag -->
			<div
				class="absolute h-full bg-blue-500 rounded-full"
				style="left: {calculatePosition(nearest)}%; right: {100 - calculatePosition(farthest)}%"
			/>

			<!-- svelte-ignore element_invalid_self_closing_tag -->
			<div
				class="absolute w-4 h-4 bg-white border-2 border-blue-500 rounded-full -mt-1 cursor-pointer hover:scale-110 transition-transform"
				style="left: calc({calculatePosition(nearest)}% - 0.5rem)"
			/>
			<!-- svelte-ignore element_invalid_self_closing_tag -->
			<div
				class="absolute w-4 h-4 bg-white border-2 border-blue-500 rounded-full -mt-1 cursor-pointer hover:scale-110 transition-transform"
				style="left: calc({calculatePosition(farthest)}% - 0.5rem)"
			/>
		</div>

		<div class="flex justify-between mt-2 text-sm text-gray-600">
			<span>{formatNumber(nearest)} km</span>
			<span>{formatNumber(farthest)} km</span>
		</div>
	</div>
</div>

<script lang="ts">
	let nearest: number = 0.1;
	let farthest: number = 10;

	function updateNearest(value: number) {
		nearest = value;
		if (nearest > farthest) {
			farthest = nearest;
		}
	}

	function updateFarthest(value: number) {
		farthest = value;
		if (farthest < nearest) {
			nearest = farthest;
		}
	}

	function formatNumber(num: number): string {
		return Number(num.toFixed(1)).toString();
	}
</script>

<div>
	<h1 class="text-xl font-semibold text-black mb-3">Distance</h1>
	<div class="bg-white rounded-lg shadow-sm py-4">
		<div class="flex items-center justify-between gap-4 mb-2">
			<div class="flex-1">
				<label for="nearest" class="block text-sm text-gray-600 mb-1">Nearest</label>
				<div class="relative">
					<input
						type="number"
						id="nearest"
						value={nearest}
						on:input={(e) => updateNearest(parseFloat(e.currentTarget.value))}
						min="0.1"
						max={farthest}
						step="0.1"
						class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 appearance-none"
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
						on:input={(e) => updateFarthest(parseFloat(e.currentTarget.value))}
						min={nearest}
						max="100"
						step="0.1"
						class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500 appearance-none"
					/>
					<span class="absolute right-3 top-1/2 -translate-y-1/2 text-gray-500">km</span>
				</div>
			</div>
		</div>

		<div class="relative w-full h-2 bg-gray-200 rounded-full mt-6">
			<div
				class="absolute h-full bg-blue-500 rounded-full"
				style="left: {(nearest / 100) * 100}%; right: {100 - (farthest / 100) * 100}%"
			></div>
			<div
				class="absolute w-4 h-4 bg-white border-2 border-blue-500 rounded-full -mt-1 cursor-pointer"
				style="left: calc({(nearest / 100) * 100}% - 0.5rem)"
			></div>
			<div
				class="absolute w-4 h-4 bg-white border-2 border-blue-500 rounded-full -mt-1 cursor-pointer"
				style="left: calc({(farthest / 100) * 100}% - 0.5rem)"
			></div>
		</div>

		<!-- Current Values Display -->
		<div class="flex justify-between mt-2 text-sm text-gray-600">
			<span>{formatNumber(nearest)} km</span>
			<span>{formatNumber(farthest)} km</span>
		</div>
	</div>
</div>

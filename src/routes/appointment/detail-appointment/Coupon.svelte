<script lang="ts">
	import kupon from '../img/kupon.svg';
</script>

<div>
	<h1 class="font-semibold text-lg mb-6">Apply Coupon</h1>
	<div class=" rounded-lg flex items-center border border-gray-300 w-full max-w-md">
		<!-- Coupon Icon -->
		<img class="w-6 h-6 mx-3" src={kupon} alt="Coupon Icon" />

		<!-- Coupon Code -->
		<p class="uppercase text-lg flex-grow text-gray-800">DISC20PERCEN</p>

		<!-- Apply Button -->
		<button class="bg-[#363062] text-white text-sm font-medium py-4 px-4 rounded-r-lg">
			Apply
		</button>
	</div>
	<p class="text-slate-400 text-sm mt-3">Coupon is active</p>
</div>

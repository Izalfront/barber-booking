<script lang="ts">
	import HistoryBooking from './history/HistoryBooking.svelte';

	let activeTab: string = 'Active booking';
</script>

<div class="flex justify-center items-center mb-4">
	<div class="flex space-x-4 bg-[#EDEFFB] p-1 rounded-full">
		<button
			class="p-2 rounded-full {activeTab === 'Active booking'
				? 'bg-white text-gray-800 shadow-md px-6 font-medium'
				: 'bg-transparent text-[#6B7280] px-6 font-medium'}"
			on:click={() => (activeTab = 'Active booking')}
		>
			Active booking
		</button>
		<button
			class="p-2 rounded-full {activeTab === 'History'
				? 'bg-white text-gray-800 shadow-md px-12 font-medium'
				: 'bg-transparent text-[#6B7280] px-12 font-medium'}"
			on:click={() => (activeTab = 'History')}
		>
			History
		</button>
	</div>
</div>

<div class="bg-white p-4">
	{#if activeTab === 'Active booking'}
		<h2 class="text-lg font-medium mb-4">Active Bookings</h2>
		<!-- Add your active booking content here -->
	{:else}
		<HistoryBooking />
	{/if}
</div>

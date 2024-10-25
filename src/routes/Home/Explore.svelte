<script lang="ts">
	import Filter from '../Find-barber/Filter.svelte';
	import search from './img/explore.svg';
	import filter from './img/filter.svg';

	let isFocused = false;
	let isFilter = false;

	function PopUpFilter() {
		isFilter = !isFilter;
	}
</script>

<div class="flex items-center mt-7 justify-between">
	<div class="relative">
		<!-- Icon Search -->
		<img
			class="absolute pt-4 w-9 pl-3 transition-opacity duration-200"
			src={search}
			alt="Search Icon"
			class:hidden={isFocused}
		/>

		<!-- Input Field -->
		<input
			class="bg-[#EBF0F5] p-4 sm:w-[24rem] w-[19.4rem] rounded-lg"
			type="text"
			class:pl-12={!isFocused}
			placeholder="Search barber’s, haircut service..."
			on:focus={() => (isFocused = true)}
			on:blur={() => (isFocused = false)}
		/>
	</div>
	<div>
		<!-- svelte-ignore a11y_click_events_have_key_events -->
		<!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
		<img on:click={PopUpFilter} class="bg-[#363062] p-4 rounded-lg ml-2" src={filter} alt="" />
		{#if isFilter}
			<div class="absolute top-72 right-0 z-50 w-full">
				<Filter />
			</div>
		{/if}
	</div>
</div>

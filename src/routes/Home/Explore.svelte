<script lang="ts">
	import search from './img/explore.svg';
	import filter from './img/filter.svg';

	let isFocused = false;
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
		<img class="bg-[#363062] p-4 rounded-lg ml-2" src={filter} alt="" />
	</div>
</div>

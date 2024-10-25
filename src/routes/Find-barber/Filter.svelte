<script lang="ts">
	import question from './img/qna.svg';
	import close from './img/close.svg';
	import Rating from './rating/Rating.svelte';
	import Distance from './distance/Distance.svelte';

	let activeTab = 'basic_haircut';
	let isFilter = true;

	function handleTabClick(tabName: string) {
		activeTab = tabName;
	}

	function closeClick() {
		isFilter = false;
	}

	const filterItems = [
		{ id: 'basic_haircut', label: 'Basic haircut' },
		{ id: 'coloring', label: 'Coloring' },
		{ id: 'treatment', label: 'Treatment' },
		{ id: 'massage', label: 'Massage' },
		{ id: 'kids_haircut', label: 'Kids haircut' }
	];
</script>

{#if isFilter}
	<div class="w-full max-w-[500px] mx-auto text-base overflow-x-hidden h-screen">
		<div
			class="bg-black/20 -z-10 p-12 bottom-[90%] absolute w-full max-w-[500px] mx-auto overflow-x-hidden h-screen"
		></div>
		<div class="bg-white shadow-lg w-full border rounded-t-3xl h-full">
			<div class="flex justify-between items-center py-6 px-8 bg-[#EDEFFB] rounded-t-3xl">
				<div class="flex gap-x-6 items-center">
					<img class="bg-white rounded-xl p-4" src={question} alt="" />
					<h1 class="text-2xl font-semibold text-black">Filter</h1>
				</div>

				<!-- svelte-ignore a11y_click_events_have_key_events -->
				<div>
					<!-- svelte-ignore a11y_click_events_have_key_events -->
					<!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
					<img on:click={closeClick} src={close} alt="" />
				</div>
			</div>
			<div class="bg-white p-8">
				<h1 class="text-xl font-semibold text-black">General Category</h1>
				<div class="mt-3 grid grid-cols-3 gap-4">
					{#each filterItems as filter}
						<div>
							<button
								class={` ${activeTab === filter.id ? 'text-[#363062] bg-[#EDEFFB] p-1.5 border border-black rounded-lg' : 'text-[#8683A1] p-1.5'}`}
								on:click={() => handleTabClick(filter.id)}
							>
								{filter.label}
							</button>
						</div>
					{/each}
				</div>
			</div>
			<div class="px-8">
				<Rating />
				<Distance />
				<button class="bg-[#363062] text-white p-4 rounded-xl w-full font-medium">Apply</button>
			</div>
		</div>
	</div>
{/if}

<style>
	.active {
		background-color: #edeffb;
		padding: 2;
	}

	.active-text {
		color: #363062;
		font-weight: 600;
	}
</style>

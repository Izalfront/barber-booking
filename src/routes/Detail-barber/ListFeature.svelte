<script lang="ts">
	import about from './img/people_nearby.svg';
	import cut from './img/Scissors.svg';
	import review from '../home/img/rating.svg';
	import schedule from './img/schedule.svg';
	import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();

	let dataFeatures = [
		{
			id: 'about',
			title: 'About',
			img: about
		},
		{
			id: 'service',
			title: 'Serivce',
			img: cut
		},
		{
			id: 'schedule',
			title: 'Schedule',
			img: schedule
		},
		{
			id: 'review',
			title: 'Review',
			img: review
		}
	];

	let activeFeature = '';

	function handleClickFeat(tabName: string) {
		activeFeature = tabName;
		dispatch('change', activeFeature);
	}
</script>

<div class="flex gap-4 overflow-x-auto no-scrollbar p-3">
	{#each dataFeatures as data}
		<!-- svelte-ignore a11y_click_events_have_key_events -->
		<!-- svelte-ignore a11y_no_static_element_interactions -->
		<div
			on:click={() => handleClickFeat(data.id)}
			class={`${activeFeature == data.id ? 'flex justify-center items-center gap-2 px-6 py-1 rounded-lg border-2 border-black min-w-[120px]' : 'flex items-center gap-2 px-6 py-1 min-w-[120px]'}`}
		>
			<img
				class={`${activeFeature == data.id ? 'w-6 h-6 brightness-50' : 'w-6 h-6'}`}
				src={data.img}
				alt={data.title}
			/>

			<p
				class={`${activeFeature == data.id ? 'text-sm font-medium text-gray-700' : 'text-sm font-medium text-gray-500'}`}
			>
				{data.title}
			</p>
		</div>
	{/each}
</div>

<style>
	.no-scrollbar::-webkit-scrollbar {
		display: none;
	}

	.no-scrollbar {
		-ms-overflow-style: none;
		scrollbar-width: none;
	}

	.active {
		background-color: #edeffb;
		padding: 2;
	}

	.active-text {
		color: #363062;
		font-weight: 600;
	}
</style>

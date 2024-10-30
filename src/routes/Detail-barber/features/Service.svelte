<script lang="ts">
	import basic from '../img/basic-haircut.png';
	import kids from '../img/kids-haircut.png';
	import coloring from '../img/hair-coloring.png';
	import treatment from '../img/hair-treatment.png';
	import special from '../img/special-message.png';

	let service = [
		{
			id: 'basic-haircut',
			title: 'Basic Haircut',
			special: 'Basic haircut & vitamint',
			salary: 20,
			img: basic
		},
		{
			id: 'kids-haircut',
			title: 'Kids Haircut',
			special: 'Special kids haircut',
			salary: 15,
			img: kids
		},
		{
			id: 'hair-coloring',
			title: 'Hair Coloring',
			special: 'Hair color treatment',
			salary: 30,
			img: coloring
		},
		{
			id: 'hair-treatment',
			title: 'Hair treatment',
			special: 'Basic haircut & vitamint',
			salary: 10,
			img: treatment
		},
		{
			id: 'special-message',
			title: 'Special massage',
			special: 'Additional massage',
			salary: 10,
			img: special
		}
	];
</script>

<div>
	<h1 class="text-xl font-semibold text-black">Our Service</h1>
	<div class="mt-6">
		{#each service as data}
			<!-- svelte-ignore a11y_click_events_have_key_events -->
			<!-- svelte-ignore a11y_no_static_element_interactions -->
			<div
				class="flex justify-between items-center"
				onclick={() => {
					data.id;
				}}
			>
				<div class="flex gap-2 mb-6">
					<div class="text-start">
						<img class="size-14" src={data.img} alt="" />
					</div>
					<div class="text-start">
						<h1 class="text-lg font-semibold">{data.title}</h1>
						<p class="text-slate-500">{data.special}</p>
					</div>
				</div>
				<div class="flex items-center gap-x-2">
					<p class="text-black">${data.salary}</p>
				</div>
			</div>
		{/each}
	</div>
</div>

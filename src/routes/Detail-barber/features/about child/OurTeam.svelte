<script lang="ts">
	import emanuel from '../../img/emanuel.png';
	import luther from '../../img/luther.png';
	import karl from '../../img/karl.png';
	import rating from '../../../home/img/rating.svg';
	let people = [
		{
			name: 'Luther Hammes',
			skill: 'Specialist Haircut',
			image: luther,
			rating: 50
		},
		{
			name: 'Emanuel Bernier',
			skill: 'Specialist Coloring',
			image: emanuel,
			rating: 4.9
		},
		{
			name: 'Karl Vandervort',
			skill: 'Specialist Treatment',
			image: karl,
			rating: 4.8
		}
	];
</script>

<div class="mt-6">
	<h1 class="text-xl font-semibold text-black">Our Team</h1>
	<div class="mt-6">
		{#each people as data}
			<div class="flex justify-between items-center">
				<div class="flex gap-2 mb-6">
					<img class="size-14" src={data.image} alt="" />
					<div class="text-start">
						<h1 class="text-lg font-semibold">{data.name}</h1>
						<p class="text-slate-500">{data.skill}</p>
					</div>
				</div>
				<div class="flex items-center gap-x-2">
					<img class="size-4" src={rating} alt="" />
					<p class="text-slate-500">{data.rating}</p>
				</div>
			</div>
		{/each}
	</div>
</div>

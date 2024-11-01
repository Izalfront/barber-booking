<script lang="ts">
	import history1 from '../img/history1.png';
	import history2 from '../img/history2.png';
	import history3 from '../img/history3.png';
	import history4 from '../img/history4.png';
	import rating from '../../home/img/rating.svg';
	import location from '../img/locationhistory.svg';
	let historys = [
		{
			title: 'Varcity Barbershop Jogja ex The Varcher',
			location: 'Condongcatur (10 km)',
			rating: '4.5',
			img: history1
		},
		{
			title: 'Varcity Barbershop Jogja ex The Varcher',
			location: 'Jl Taman Siswa (8 km)',
			rating: '5.0',
			img: history2
		},
		{
			title: 'Varcity Barbershop Jogja ex The Varcher',
			location: 'J-Walk Centre  (17 km)',
			rating: '4.5',
			img: history3
		},
		{
			title: 'Varcity Barbershop Jogja ex The Varcher',
			location: 'Banguntapan (5 km)',
			rating: '4.5',
			img: history4
		}
	];
</script>

<div class="mt-3">
	{#each historys as data}
		<div class="flex mt-5">
			<div class="mr-3">
				<img class="w-36 h-auto" src={data.img} alt="" />
			</div>
			<div class="flex flex-col">
				<h1 class="font-semibold text-lg">{data.title}</h1>
				<div class="flex gap-2">
					<img src={location} alt="" />
					<p class="text-slate-500">{data.location}</p>
				</div>
				<div class="flex gap-2">
					<img src={rating} alt="" />
					<p class="text-slate-500">{data.rating}</p>
				</div>
			</div>
		</div>
	{/each}
</div>

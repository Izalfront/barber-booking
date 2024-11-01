<script lang="ts">
	import cut from '../img/Scissors.svg';
	import barber1 from '../img/bookingservice1.png';
	import barber2 from '../img/bookingservice2.png';
	import people from '../../BottomBar/img/profil.svg';
	import luther from '../../detail-barber/img/luther.png';
	let bookingService = [
		{
			title: 'Basic haircut',
			booking: 'Basic haircut & vitamint',
			img: barber1
		},
		{
			title: 'Massage',
			booking: 'Extra massage',
			img: barber2
		}
	];
</script>

<div>
	<div class="flex gap-2">
		<img src={cut} alt="" />
		<h1 class="font-semibold text-lg">Service selected</h1>
	</div>
	{#each bookingService as data}
		<div class="flex my-4">
			<img class="w-14 h-auto mr-2" src={data.img} alt="" />
			<div>
				<h1 class="font-semibold text-lg">{data.title}</h1>
				<p class="text-slate-500">{data.booking}</p>
			</div>
		</div>
	{/each}
	<div class="flex gap-2 mt-8">
		<img class="brightness-0" src={people} alt="" />
		<h1 class="font-semibold text-lg">Master barber</h1>
	</div>
	<div class="flex mt-4">
		<img class="w-14 h-auto mr-2" src={luther} alt="" />
		<div>
			<h1 class="font-semibold text-lg">Luther Hammes</h1>
			<p class="text-slate-500">Specialist Haircut</p>
		</div>
	</div>
</div>

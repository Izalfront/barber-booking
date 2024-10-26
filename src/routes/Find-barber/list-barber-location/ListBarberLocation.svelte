<script lang="ts">
	import pinned from '../../home/img/pinned.svg';
	let dataBarber = [
		{
			id: 'barbershop_1',
			name: 'dataBarber',
			address: 'Banjarmasin kayu tangi 2',
			route: 'Jl. Kayu tangi 2',
			location: 'https://youtube.com'
		},
		{
			id: 'barbershop_2',
			name: 'dataBarber',
			address: 'Banjarmasin kayu tangi 2',
			route: 'Jl. Kayu tangi 2',
			location: 'https://youtube.com'
		},
		{
			id: 'barbershop_3',
			name: 'dataBarber',
			address: 'Banjarmasin kayu tangi 2',
			route: 'Jl. Kayu tangi 2',
			location: 'https://youtube.com'
		}
	];

	let activeLocation = '';
	function handleCLickLocation(tabName: string) {
		activeLocation = tabName;
	}
</script>

<div class="block">
	<h1 class="text-xl font-semibold my-4">Recent location</h1>
	{#each dataBarber as barber}
		<a
			href={barber.location}
			target="_blank"
			rel="noopener noreferrer"
			on:click={() => handleCLickLocation(barber.id)}
			class={`${activeLocation == barber.id ? 'my-3 bg-[#EDEFFB] border-2 rounded-xl px-5 py-3 block' : 'my-3 bg-white border-2 rounded-xl px-5 py-3 block'}`}
		>
			<div class="flex gap-x-2 items-center">
				<img src={pinned} alt="" />
				<h1 class="text-lg font-semibold">{barber.name}</h1>
			</div>
			<div class="flex gap-x-1 text-[#6B7280]">
				<p>{barber.route}</p>
				<p>{barber.address}</p>
			</div>
		</a>
	{/each}
</div>

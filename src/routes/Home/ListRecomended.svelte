<script lang="ts">
	import barber from './img/recomend2.png';
	import barber2 from './img/recomend1.png';
	import barber3 from './img/recomend3.png';

	let listBarber = [
		{
			title: `Varcity Barbershop Jogja ex The Varcher`,
			pinned: 'Condongcatur (10 km)',
			rating: '5.0',
			img: barber
		},
		{
			title: `Twinsky Monkey Barber & Men Stuff`,
			pinned: 'Jl Taman Siswa (8 km)',
			rating: '4.9',
			img: barber2
		},
		{
			title: `Barberman - Haircut styling & massage`,
			pinned: 'J-Walk Centre  (17 km)',
			rating: '4.8',
			img: barber3
		},
		{
			title: 'Alana Barbershop - Haircut massage & Spa',
			pinned: 'Banguntapan (5 km)',
			rating: '4.7',
			img: barber
		},
		{
			title: `Hercha Barbershop - Haircut & Styling`,
			pinned: 'Jalan Kaliurang (8 km)',
			rating: '4.7',
			img: barber2
		},
		{
			title: 'Alana Barbershop - Haircut massage & Spa',
			pinned: 'Banguntapan (5 km)',
			rating: '4.6',
			img: barber3
		}
	];

	function getDisplayedItems() {
		return listBarber.filter((_, index) => index < displayCount);
	}

	$: displayCount = 3;

	$: displayedItems = listBarber.slice(0, displayCount);

	function handleShowAll() {
		displayCount = listBarber.length;

		displayedItems = [...listBarber];
	}

	$: showButton = displayCount < listBarber.length;
</script>

<div class="mt-4">
	{#each getDisplayedItems() as list}
		<div class="flex items-start mt-4">
			<img class="w-auto h-28 mr-2" src={list.img} alt="" />
			<div>
				<h1 class="font-semibold text-lg leading-tight mb-2">
					{list.title}
				</h1>
				<div class="flex items-center">
					<svg
						width="12"
						height="14"
						viewBox="0 0 12 14"
						fill="currentColor"
						xmlns="http://www.w3.org/2000/svg"
						class="text-[#8683A1] mr-2"
					>
						<path
							fill-rule="evenodd"
							clip-rule="evenodd"
							d="M5.99984 0.333252C3.05432 0.333252 0.666504 3.00164 0.666504 5.99992C0.666504 8.9747 2.36872 12.2082 5.02455 13.4495C5.64367 13.7389 6.35601 13.7389 6.97513 13.4495C9.63095 12.2082 11.3332 8.9747 11.3332 5.99992C11.3332 3.00164 8.94536 0.333252 5.99984 0.333252ZM5.99984 6.99992C6.73622 6.99992 7.33317 6.40297 7.33317 5.66659C7.33317 4.93021 6.73622 4.33325 5.99984 4.33325C5.26346 4.33325 4.6665 4.93021 4.6665 5.66659C4.6665 6.40297 5.26346 6.99992 5.99984 6.99992Z"
						/>
					</svg>
					<p class="text-[#8683A1]">{list.pinned}</p>
				</div>
				<div class="flex items-center">
					<svg
						width="15"
						height="14"
						viewBox="0 0 15 14"
						fill="currentColor"
						xmlns="http://www.w3.org/2000/svg"
						class="text-[#8683A1] mr-2"
					>
						<path
							d="M5.60227 2.6055C6.44671 1.09067 6.86892 0.333252 7.50016 0.333252C8.1314 0.333252 8.55362 1.09067 9.39805 2.6055L9.61652 2.99741C9.85648 3.42788 9.97646 3.64311 10.1635 3.78512C10.3506 3.92714 10.5836 3.97985 11.0496 4.08528L11.4738 4.18127C13.1136 4.55229 13.9335 4.7378 14.1285 5.36507C14.3236 5.99235 13.7647 6.64597 12.6468 7.9532L12.3576 8.2914C12.0399 8.66288 11.881 8.84861 11.8096 9.0784C11.7381 9.30818 11.7621 9.55599 11.8102 10.0516L11.8539 10.5028C12.0229 12.247 12.1074 13.1191 11.5967 13.5067C11.086 13.8944 10.3184 13.5409 8.78305 12.834L8.38584 12.6511C7.94955 12.4503 7.7314 12.3498 7.50016 12.3498C7.26893 12.3498 7.05078 12.4503 6.61449 12.6511L6.21728 12.834C4.68195 13.5409 3.91428 13.8944 3.4036 13.5067C2.89291 13.1191 2.97742 12.247 3.14643 10.5029L3.19015 10.0516C3.23818 9.55599 3.26219 9.30818 3.19074 9.0784C3.11928 8.84861 2.96045 8.66288 2.64278 8.2914L2.35356 7.9532C1.23566 6.64597 0.676712 5.99235 0.871777 5.36507C1.06684 4.7378 1.88673 4.55229 3.52652 4.18127L3.95075 4.08528C4.41673 3.97985 4.64972 3.92714 4.83679 3.78512C5.02387 3.64311 5.14385 3.42788 5.38381 2.99741L5.60227 2.6055Z"
						/>
					</svg>
					<p class="text-[#8683A1]">{list.rating}</p>
				</div>
			</div>
		</div>
	{/each}
	{#if showButton}
		<div class="flex items-center justify-center my-6">
			<button
				class="flex items-center bg-white py-2 px-4 border border-black text-black rounded-lg"
				on:click={handleShowAll}
				>See All
				<svg
					class="ml-2"
					width="25"
					height="24"
					viewBox="0 0 25 24"
					fill="none"
					xmlns="http://www.w3.org/2000/svg"
				>
					<path
						d="M9.5 15L15.5 9M15.5 9H11M15.5 9V13.5"
						stroke="#363062"
						stroke-width="1.5"
						stroke-linecap="round"
						stroke-linejoin="round"
					/>
					<path
						d="M2.5 12C2.5 7.28595 2.5 4.92893 3.96447 3.46447C5.42893 2 7.78595 2 12.5 2C17.214 2 19.5711 2 21.0355 3.46447C22.5 4.92893 22.5 7.28595 22.5 12C22.5 16.714 22.5 19.0711 21.0355 20.5355C19.5711 22 17.214 22 12.5 22C7.78595 22 5.42893 22 3.96447 20.5355C2.5 19.0711 2.5 16.714 2.5 12Z"
						stroke="#363062"
						stroke-width="1.5"
					/>
				</svg>
			</button>
		</div>
	{/if}
</div>

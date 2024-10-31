<script lang="ts">
	import { writable } from 'svelte/store';
	import arrow from './img/arrow-lefting.svg';
	const days = ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'];
	const months = [
		'Januari',
		'Februari',
		'Maret',
		'April',
		'Mei',
		'Juni',
		'Juli',
		'Agustus',
		'September',
		'Oktober',
		'November',
		'Desember'
	];

	let currentDate = new Date();
	let currentMonth = writable(currentDate.getMonth());
	let currentYear = writable(currentDate.getFullYear());
	let selectedDate = writable<number | null>(null);

	// Fungsi untuk mendapatkan jumlah hari dalam bulan tertentu
	const getDaysInMonth = (month: number, year: number) => {
		return new Date(year, month + 1, 0).getDate();
	};

	// Fungsi untuk mendapatkan hari pertama dalam bulan
	const getStartDay = (month: number, year: number) => {
		return new Date(year, month, 1).getDay();
	};

	// Mengubah bulan saat tombol navigasi diklik
	const updateMonth = (change: number) => {
		currentMonth.update((value) => {
			let newMonth = value + change;
			if (newMonth < 0) {
				currentYear.update((year) => year - 1);
				return 11;
			} else if (newMonth > 11) {
				currentYear.update((year) => year + 1);
				return 0;
			}
			return newMonth;
		});
		selectedDate.set(null); // Menghapus pilihan saat bulan diubah
	};

	// Memilih tanggal tertentu
	const selectDate = (day: number) => {
		selectedDate.set(day);
	};
</script>

<div class="max-w-md mx-auto p-4">
	<!-- Bagian Header Kalender -->
	<div
		class="flex items-center justify-between rounded-t-md px-6 py-3 rounded-lg bg-[#EDEFFB] mb-3"
	>
		<button on:click={() => updateMonth(-1)} class="text-gray-600 hover:text-gray-900">
			<div>
				<img src={arrow} alt="" />
			</div>
		</button>
		<div class="text-lg font-medium">
			<span>{months[$currentMonth]} {$currentYear}</span>
		</div>
		<button on:click={() => updateMonth(1)} class="text-gray-600 hover:text-gray-900 rounded-lg">
			<div class="-scale-x-[1]">
				<img src={arrow} alt="" />
			</div>
		</button>
	</div>

	<!-- Grid untuk Hari dan Tanggal -->
	<div class="grid grid-cols-7 rounded-b-md">
		{#each days as day}
			<div class="text-center py-2">{day}</div>
		{/each}

		{#each Array(getStartDay($currentMonth, $currentYear)).fill(0) as _}
			<div class="py-2 font-semibold"></div>
		{/each}

		<!-- svelte-ignore a11y_no_static_element_interactions -->
		{#each Array(getDaysInMonth($currentMonth, $currentYear)) as _, i}
			<!-- svelte-ignore a11y_click_events_have_key_events -->
			<div
				class="p-2 text-center font-semibold text-lg cursor-pointer transition-all duration-200"
				class:font-bold={i + 1 === $selectedDate}
				class:bg-[#363062]={i + 1 === $selectedDate}
				class:text-white={i + 1 === $selectedDate}
				class:rounded-full={i + 1 === $selectedDate}
				on:click={() => selectDate(i + 1)}
			>
				{i + 1}
			</div>
		{/each}
	</div>
</div>

<style>
	@media (max-width: 768px) {
		.grid {
			grid-template-columns: repeat(7, 1fr);
		}
	}
</style>

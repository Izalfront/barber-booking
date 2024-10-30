<script lang="ts">
	import { writable } from 'svelte/store';

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
	<div class="flex items-center justify-between bg-gray-100 rounded-t-md px-4 py-2">
		<button on:click={() => updateMonth(-1)} class="text-gray-600 hover:text-gray-900">
			&#x25C0;
		</button>
		<div class="text-lg font-medium">
			<span>{months[$currentMonth]} {$currentYear}</span>
		</div>
		<button on:click={() => updateMonth(1)} class="text-gray-600 hover:text-gray-900">
			&#x25B6;
		</button>
	</div>

	<!-- Grid untuk Hari dan Tanggal -->
	<div class="grid grid-cols-7 bg-gray-100 rounded-b-md">
		{#each days as day}
			<div class="text-center py-2 font-semibold">{day}</div>
		{/each}

		{#each Array(getStartDay($currentMonth, $currentYear)).fill(0) as _}
			<div class="py-2"></div>
		{/each}

		<!-- svelte-ignore a11y_no_static_element_interactions -->
		{#each Array(getDaysInMonth($currentMonth, $currentYear)) as _, i}
			<!-- svelte-ignore a11y_click_events_have_key_events -->
			<div
				class="py-2 text-center cursor-pointer transition-all duration-200"
				class:font-bold={i + 1 === $selectedDate}
				class:bg-purple-600={i + 1 === $selectedDate}
				class:text-white={i + 1 === $selectedDate}
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

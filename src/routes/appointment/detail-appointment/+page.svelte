<script lang="ts">
	import pattern from '../img/pattern.png';
	import master from '../img/masterpc.png';

	import pay from '../img/pay.svg';
	import date from '../img/date.svg';
	import cut from '../img/Scissors.svg';
	import message from '../img/message.png';
	import Coupon from './Coupon.svelte';
	import PaymentSummary from './PaymentSummary.svelte';
	import { goto } from '$app/navigation';

	function goToDetailBarber() {
		goto('/appointment');
	}

	function goToInvoice() {
		goto('/appointment/detail-appointment/invoice');
	}

	let order = [
		{
			id: 1,
			title: 'Basic haircut',
			desc: 'Basic haircut & vitamint',
			salary: '$20',
			img: message
		},
		{
			id: 2,
			title: 'Massage',
			desc: 'Extra massage',
			salary: '$10',
			img: message
		}
	];
</script>

<div class="w-full max-w-[450px] mx-auto text-base h-screen bg-[#363062] overflow-y-auto">
	<!-- Header - Fixed at top -->
	<!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
	<div class="sticky top-0 bg-[#363062] p-6 z-20">
		<!-- svelte-ignore a11y_click_events_have_key_events -->
		<h1
			on:click={goToDetailBarber}
			class="text-xl font-semibold my-6 flex gap-x-4 items-center text-white cursor-pointer"
		>
			<svg
				width="18"
				height="14"
				viewBox="0 0 18 14"
				fill="none"
				xmlns="http://www.w3.org/2000/svg"
			>
				<path
					d="M17 7H1M1 7L7 1M1 7L7 13"
					stroke="#fff"
					stroke-width="2"
					stroke-linecap="round"
					stroke-linejoin="round"
				/>
			</svg>
			Your Appointment
		</h1>
	</div>

	<!-- Main Content -->
	<div class="relative min-h-[calc(100vh-116px)]">
		<!-- Background pattern -->
		<img class="w-full h-48 object-cover" src={pattern} alt="Pattern background" />

		<!-- Top Card -->
		<div class="absolute top-4 left-4 right-4 bg-white/20 rounded-lg shadow-lg p-4">
			<div class="flex items-center gap-4">
				<div class="w-24 h-24 flex-shrink-0 overflow-hidden rounded-lg">
					<img class="w-full h-full object-cover" src={master} alt="Masterimage" />
				</div>

				<div class="text-white">
					<h1 class="font-semibold text-lg">Master piece Barbershop - Haircut styling</h1>
					<div class="flex flex-col text-sm mt-2">
						<p>Jogja Expo Centre (2 km)</p>
						<p>5.0 (24)</p>
					</div>
				</div>
			</div>
		</div>

		<!-- Bottom Card -->
		<div
			class="absolute top-48 left-0 right-0 bg-white rounded-t-3xl p-6 min-h-[calc(100vh-192px)]"
		>
			<!-- Date & Time -->
			<div class="flex flex-col">
				<div class="flex gap-3 items-center">
					<img src={date} alt="" class="w-6 h-6" />
					<h1 class="font-semibold text-lg">Date & time</h1>
				</div>
				<div class="mt-2">
					<p class="text-lg text-slate-500">Sun, 15 Jan - 08:00 AM</p>
				</div>
			</div>

			<!-- Service List -->
			<div class="mt-6">
				<div class="flex gap-3 items-center">
					<img src={cut} alt="" class="w-6 h-6" />
					<h1 class="text-lg font-semibold">Service lists</h1>
				</div>
				{#each order as data}
					<div class="flex justify-between items-center mt-6">
						<div class="flex items-center gap-3">
							<div class="w-14 h-14">
								<img src={data.img} alt="" class="w-full h-full object-cover" />
							</div>
							<div>
								<h1 class="font-semibold text-lg">{data.title}</h1>
								<p class="text-slate-500">{data.desc}</p>
							</div>
						</div>
						<div>
							<h1 class="font-semibold text-lg">{data.salary}</h1>
						</div>
					</div>
				{/each}

				<!-- Coupon -->
				<div class="mt-6">
					<Coupon />
				</div>

				<!-- Payment Summary -->
				<div class="mt-6 mb-6">
					<PaymentSummary />
				</div>
				<div>
					<button
						on:click={goToInvoice}
						class="w-full h-14 rounded-xl text-white font-semibold bg-[#363062] mt-4 tracking-wide flex items-center justify-center gap-2"
						>Deal booking <img src={pay} alt="" /></button
					>
				</div>
			</div>
		</div>
	</div>
</div>

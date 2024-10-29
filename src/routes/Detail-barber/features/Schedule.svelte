<script lang="ts">
	import alan from '../img/alan.png';
	import robert from '../img/robert.png';
	import sergio from '../img/sergio.png';

	interface Appointment {
		id: number;
		time: string;
		name: string;
		service: string;
		image: string;
		color: string;
	}

	const timeSlots = ['08.00 am', '08.30 am', '09.00 am', '09.30 am', '10.00 am', '10.30 am'];

	const appointments: Appointment[] = [
		{
			id: 1,
			time: '08.00 am',
			name: 'Alam Carl',
			service: 'Basic haircut',
			image: alan,
			color: 'bg-orange-400'
		},
		{
			id: 2,
			time: '09.00 am',
			name: 'Sergio Wirl',
			service: 'Hair coloring',
			image: robert,
			color: 'bg-purple-400'
		},
		{
			id: 3,
			time: '10.00 am',
			name: 'Sergio Wirl',
			service: 'Basic haircut',
			image: sergio,
			color: 'bg-purple-400'
		}
	];

	const getAppointment = (time: string) => {
		return appointments.find((app) => app.time === time);
	};

	// Current date
	const currentDate = new Date();
	const formattedDate = currentDate.toLocaleDateString('en-US', {
		day: '2-digit',
		month: 'short',
		year: 'numeric'
	});
</script>

<div class="p-4 max-w-md mx-auto">
	<!-- Date Header -->
	<div class="flex items-center gap-2 mb-6">
		<svg
			xmlns="http://www.w3.org/2000/svg"
			class="h-6 w-6"
			fill="none"
			viewBox="0 0 24 24"
			stroke="currentColor"
		>
			<path
				stroke-linecap="round"
				stroke-linejoin="round"
				stroke-width="2"
				d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"
			/>
		</svg>
		<span class="font-semibold">{formattedDate}</span>
	</div>

	<!-- Timeline Header -->
	<h2 class="text-xl font-semibold mb-4">Timeline</h2>

	<!-- Timeline Container -->
	<div class="relative">
		<!-- Vertical Line -->
		<div class="absolute left-[4.5rem] top-0 bottom-0 w-px bg-gray-200"></div>

		<!-- Time Slots -->
		{#each timeSlots as time}
			<div class="relative flex items-center mb-8">
				<!-- Time -->
				<div class="w-20 text-sm text-gray-600">{time}</div>

				<!-- Dot -->
				<div class="absolute left-[4.5rem] w-2 h-2 rounded-full bg-gray-300 -translate-x-1"></div>

				<!-- Appointment Card -->
				{#if getAppointment(time)}
					{@const appointment = getAppointment(time)}
					<div class="ml-8 flex-1">
						<div class="rounded-xl p-3 {appointment?.color} text-white">
							<div class="flex items-center gap-2">
								<img
									src={appointment?.image}
									alt={appointment?.name}
									class="w-10 h-10 rounded-full border-2 border-white"
								/>
								<div>
									<h3 class="font-semibold">{appointment?.name}</h3>
									<p class="text-sm text-white/90">{appointment?.service}</p>
								</div>
							</div>
						</div>
					</div>
				{/if}
			</div>
		{/each}
	</div>
	<div>
		<button class="w-full h-14 rounded-xl text-white font-semibold bg-[#363062] mt-4 tracking-wide"
			>Booking Now</button
		>
	</div>
</div>

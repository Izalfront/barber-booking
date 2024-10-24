<script lang="ts">
	import pp from './img/pprofile.png';
	import bg from '../Login/img/bg-login.svg';
	import logo from './img/logo-gobar2.png';
	import people from '../Onboarding/img/onboard3.png';
	import Explore from './Explore.svelte';
	import ListBarbershop from './ListBarbershop.svelte';
</script>

<div class="w-full max-w-[500px] mx-auto text-base overflow-x-hidden h-screen">
	<div class="mx-6">
		<!-- profile -->
		<div class="flex justify-between items-end mt-12">
			<div class="block">
				<p class="flex items-center font-normal text-[#6B7280]">
					<svg
						class="mr-2"
						width="12"
						height="14"
						viewBox="0 0 12 14"
						fill="none"
						xmlns="http://www.w3.org/2000/svg"
					>
						<path
							fill-rule="evenodd"
							clip-rule="evenodd"
							d="M5.99984 0.333252C3.05432 0.333252 0.666504 3.00164 0.666504 5.99992C0.666504 8.9747 2.36872 12.2082 5.02455 13.4495C5.64367 13.7389 6.35601 13.7389 6.97513 13.4495C9.63095 12.2082 11.3332 8.9747 11.3332 5.99992C11.3332 3.00164 8.94536 0.333252 5.99984 0.333252ZM5.99984 6.99992C6.73622 6.99992 7.33317 6.40297 7.33317 5.66659C7.33317 4.93021 6.73622 4.33325 5.99984 4.33325C5.26346 4.33325 4.6665 4.93021 4.6665 5.66659C4.6665 6.40297 5.26346 6.99992 5.99984 6.99992Z"
							fill="#363062"
						/>
					</svg>
					Yogyakarta
				</p>
				<p class="text-[1.5rem] font-semibold">Joe Samanta</p>
			</div>
			<div class="block">
				<img class="w-auto h-14" src={pp} alt="" />
			</div>
		</div>
		<!-- promo -->
		<div class="relative bg-[#F99417] rounded-lg mx-auto mt-10 w-auto h-[250px] overflow-hidden">
			<div class="absolute inset-0">
				<img class="object-cover w-full h-full" src={bg} alt="BackgroundImage" />
			</div>
			<img class="absolute top-4 left-4 w-auto h-16 z-10" src={logo} alt="Logo" />
			<button
				class="absolute top-44 left-4 bg-[#363062] hover:bg-[#2a234e] px-4 py-3 rounded-xl text-white z-20 font-semibold"
				>Booking Now</button
			>
			<img class="absolute left-[12.3rem] w-auto h-[19rem] z-30" src={people} alt="" />
		</div>
		<!-- search -->
		<div class="mx-auto">
			<Explore />
		</div>
		<!-- list barbershop -->
		<ListBarbershop />
	</div>
</div>

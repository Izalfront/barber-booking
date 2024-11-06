<script lang="ts">
	import barber from '../Home/img/master.png';
	import calendar from '../Home/img/calendar.svg';
	import StepIndicator from '../home/child/StepIndicator.svelte';
	import ListRecomended from '../home/ListRecomended.svelte';
	import Explore from '../home/Explore.svelte';
	import CategoryFilter from '../find-barber/CategoryFilter.svelte';

	let currentStep = 1;

	function handleStepChange(step: number) {
		currentStep = step;
	}

	function goToExplore() {
		window.location.href = './explore';
	}

	function goToHome() {
		window.location.href = './home';
	}
</script>

<div class="w-full max-w-[500px] mx-auto text-base overflow-x-hidden h-screen">
	<div class="pt-6 mx-6">
		<!-- svelte-ignore a11y_click_events_have_key_events -->
		<!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
		<h1 on:click={goToHome} class="text-xl font-semibold mb-4 flex gap-x-4 items-center">
			<svg
				width="18"
				height="14"
				viewBox="0 0 18 14"
				fill="none"
				xmlns="http://www.w3.org/2000/svg"
			>
				<path
					d="M17 7H1M1 7L7 1M1 7L7 13"
					stroke="#111827"
					stroke-width="2"
					stroke-linecap="round"
					stroke-linejoin="round"
				/>
			</svg>Explore Barbers
		</h1>
		<div>
			<div class="relative overflow-hidden" style="width: 100%; height: 300px;">
				<div class="absolute inset-0">
					<img class="object-cover w-full h-full rounded-xl" src={barber} alt="BarberImage" />
				</div>
				<button
					on:click={goToExplore}
					class="absolute top-[15rem] left-[12rem] bg-[#363062] hover:bg-[#2a234e] px-6 py-3 rounded-xl text-white font-semibold"
					><div class="flex gap-x-1">
						Booking Now
						<img src={calendar} alt="Calendar Icon" />
					</div>
				</button>
			</div>

			<div class="block mt-4">
				<h1 class="font-semibold text-lg leading-tight mb-2">
					Master piece Barbershop - Haircut styling
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
					<p class="text-[#8683A1]">Joga Expo Centre (2 km)</p>
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

					<p class="text-[#8683A1]">5.0</p>
				</div>
			</div>
		</div>
		<div class="flex justify-end mt-3">
			<!-- <StepIndicator totalSteps={5} {currentStep} onStepClick={handleStepChange} /> -->
		</div>
		<div class="pt-1">
			<Explore />
		</div>
		<div class="mt-3">
			<CategoryFilter />
		</div>
		<ListRecomended />
	</div>
</div>

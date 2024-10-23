<!-- Directive for handling clicks outside dropdown -->
<script context="module" lang="ts">
	export function clickOutside(node: HTMLElement): { destroy: () => void } {
		const handleClick = (event: MouseEvent) => {
			if (node && !node.contains(event.target as Node)) {
				node.dispatchEvent(new CustomEvent('click_outside'));
			}
		};

		document.addEventListener('click', handleClick, true);

		return {
			destroy() {
				document.removeEventListener('click', handleClick, true);
			}
		};
	}
</script>

<script lang="ts">
	interface CountryCode {
		code: string;
		flag: string;
		name: string;
		dial_code: string;
	}

	const countryCodes: CountryCode[] = [
		{ code: 'ID', flag: '🇮🇩', name: 'Indonesia', dial_code: '+62' },
		{ code: 'MY', flag: '🇲🇾', name: 'Malaysia', dial_code: '+60' },
		{ code: 'SG', flag: '🇸🇬', name: 'Singapore', dial_code: '+65' },
		{ code: 'TH', flag: '🇹🇭', name: 'Thailand', dial_code: '+66' },
		{ code: 'VN', flag: '🇻🇳', name: 'Vietnam', dial_code: '+84' }
	];

	let name = '';
	let email = '';
	let phoneNumber = '';
	let password = '';
	let confirmPassword = '';
	let selectedCountry: CountryCode = countryCodes[0];
	let isDropdownOpen = false;
	let isValid = false;
	let errorMessage = '';

	interface CharPositions {
		[key: number]: string;
	}

	function formatPhoneNumber(value: string): string {
		const numbers = value.replace(/\D/g, '');
		const char: CharPositions = {
			3: '-',
			7: '-',
			11: '-'
		};
		let formatted = '';

		for (let i = 0; i < numbers.length; i++) {
			formatted += numbers[i];
			if (char[i]) formatted += char[i];
		}

		return formatted;
	}

	function validatePhoneNumber(value: string): boolean {
		const digitsOnly = value.replace(/\D/g, '');

		if (digitsOnly.length < 10) {
			errorMessage = 'Phone number must be at least 10 digits';
			return false;
		}
		if (digitsOnly.length > 13) {
			errorMessage = 'Phone number cannot exceed 13 digits';
			return false;
		}

		if (selectedCountry.code === 'ID') {
			if (!digitsOnly.startsWith('08')) {
				errorMessage = 'Indonesian numbers should start with 08';
				return false;
			}
		}

		errorMessage = '';
		return true;
	}

	function handleInput(event: Event): void {
		const input = event.target as HTMLInputElement;
		let value = input.value.replace(/\D/g, '');

		if (value.length > 13) {
			value = value.slice(0, 13);
		}

		phoneNumber = formatPhoneNumber(value);
		isValid = validatePhoneNumber(phoneNumber);
	}

	function selectCountry(country: CountryCode): void {
		selectedCountry = country;
		isDropdownOpen = false;
		if (phoneNumber) {
			isValid = validatePhoneNumber(phoneNumber);
		}
	}

	function handleClickOutside(): void {
		isDropdownOpen = false;
	}

	function handleRegister(event: Event): void {
		event.preventDefault();

		if (!name || !email || !phoneNumber || !password || !confirmPassword) {
			alert('Please fill in all fields');
			return;
		}

		if (password !== confirmPassword) {
			alert('Passwords do not match');
			return;
		}

		if (!isValid) {
			alert('Please enter a valid phone number');
			return;
		}

		console.log('Registration data:', {
			name,
			email,
			phoneNumber: `${selectedCountry.dial_code}${phoneNumber}`,
			password
		});
	}

	let showPassword = false;
	let showConfirmPassword = false;

	function goToAuthentication() {
		window.location.href = '/authentication';
	}
</script>

<div class="w-full max-w-[500px] mx-auto text-base overflow-x-hidden h-screen">
	<div class="mt-24 mx-8">
		<h1 class="text-3xl font-[700] text-[#363062]">Register here</h1>
		<p class="text-xl mt-2 text-[#6B7280]">
			Please enter your data to complete your account registration process
		</p>
		<div class="grid grid-cols-1 mt-12">
			<label for="email" class="text-lg font-medium pb-2 text-[#111827]">Name</label>
			<div class="relative flex items-center">
				<input
					class="bg-white p-3 pl-10 border border-[#D1D5DB] rounded-lg w-full"
					id="name"
					type="name"
					bind:value={name}
					placeholder="Enter your name"
				/>
				<svg
					class="absolute left-3"
					width="24"
					height="24"
					viewBox="0 0 24 24"
					fill="none"
					xmlns="http://www.w3.org/2000/svg"
				>
					<circle cx="12" cy="6" r="4" fill="#363062" />
					<path
						d="M20 17.5C20 19.9853 20 22 12 22C4 22 4 19.9853 4 17.5C4 15.0147 7.58172 13 12 13C16.4183 13 20 15.0147 20 17.5Z"
						fill="#1C274C"
					/>
				</svg>
			</div>
		</div>
		<div class="grid grid-cols-1 mt-4">
			<label for="email" class="text-lg font-medium pb-2 text-[#111827]">Email</label>
			<div class="relative flex items-center">
				<input
					class="bg-white p-3 pl-10 border border-[#D1D5DB] rounded-lg w-full"
					id="email"
					type="email"
					bind:value={email}
					placeholder="Enter your email"
				/>
				<svg
					class="absolute left-3"
					width="20"
					height="16"
					viewBox="0 0 20 16"
					fill="none"
					xmlns="http://www.w3.org/2000/svg"
				>
					<path
						fill-rule="evenodd"
						clip-rule="evenodd"
						d="M1.17157 1.17157C0 2.34315 0 4.22876 0 8C0 11.7712 0 13.6569 1.17157 14.8284C2.34315 16 4.22876 16 8 16H12C15.7712 16 17.6569 16 18.8284 14.8284C20 13.6569 20 11.7712 20 8C20 4.22876 20 2.34315 18.8284 1.17157C17.6569 0 15.7712 0 12 0H8C4.22876 0 2.34315 0 1.17157 1.17157ZM16.5762 3.51986C16.8413 3.83807 16.7983 4.31099 16.4801 4.57617L14.2837 6.40657C13.3973 7.14523 12.6789 7.74392 12.0448 8.15172C11.3843 8.57653 10.7411 8.84488 10 8.84488C9.25892 8.84488 8.61567 8.57653 7.95518 8.15172C7.32112 7.74392 6.60271 7.14523 5.71636 6.40658L3.51986 4.57617C3.20165 4.31099 3.15866 3.83807 3.42383 3.51986C3.68901 3.20165 4.16193 3.15866 4.48014 3.42383L6.63903 5.22291C7.57199 6.00038 8.21973 6.53841 8.76658 6.89013C9.29594 7.23059 9.65493 7.34487 10 7.34487C10.3451 7.34487 10.7041 7.23059 11.2334 6.89013C11.7803 6.53841 12.428 6.00038 13.361 5.22291L15.5199 3.42383C15.8381 3.15866 16.311 3.20165 16.5762 3.51986Z"
						fill="#363062"
					/>
				</svg>
			</div>
		</div>
		<div class="grid grid-cols-1 mt-4">
			<label for="phone" class="text-lg font-medium pb-2 text-[#111827]">Phone number</label>
			<!-- svelte-ignore a11y_no_static_element_interactions -->
			<div class="relative flex items-center">
				<!-- svelte-ignore a11y_click_events_have_key_events -->
				<div
					class="absolute left-3 flex items-center gap-1 cursor-pointer z-20"
					on:click={() => (isDropdownOpen = !isDropdownOpen)}
				>
					<span class="text-gray-600">{selectedCountry.flag} {selectedCountry.dial_code}</span>
					<svg
						class="w-4 h-4 text-gray-400 transform transition-transform duration-200"
						class:rotate-180={isDropdownOpen}
						fill="none"
						stroke="currentColor"
						viewBox="0 0 24 24"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M19 9l-7 7-7-7"
						/>
					</svg>
				</div>

				<input
					class="bg-white p-3 pl-[6.5rem] pr-12 border border-[#D1D5DB] rounded-lg w-full
                   focus:outline-none focus:ring-2 focus:ring-[#363062] focus:border-transparent
                   {isValid ? 'border-green-500' : errorMessage ? 'border-red-500' : ''}"
					id="phone"
					type="tel"
					bind:value={phoneNumber}
					on:input={handleInput}
					placeholder="089-568-000-000"
				/>

				<!-- Validation Icon -->
				<div class="absolute right-3">
					{#if phoneNumber.length > 0}
						{#if isValid}
							<svg
								width="20"
								height="20"
								viewBox="0 0 20 20"
								fill="none"
								xmlns="http://www.w3.org/2000/svg"
								class="text-green-500"
							>
								<path
									fill-rule="evenodd"
									clip-rule="evenodd"
									d="M20 10C20 15.5228 15.5228 20 10 20C4.47715 20 0 15.5228 0 10C0 4.47715 4.47715 0 10 0C15.5228 0 20 4.47715 20 10ZM14.0303 6.96967C14.3232 7.26256 14.3232 7.73744 14.0303 8.03033L9.03033 13.0303C8.73744 13.3232 8.26256 13.3232 7.96967 13.0303L5.96967 11.0303C5.67678 10.7374 5.67678 10.2626 5.96967 9.96967C6.26256 9.67678 6.73744 9.67678 7.03033 9.96967L8.5 11.4393L10.7348 9.2045L12.9697 6.96967C13.2626 6.67678 13.7374 6.67678 14.0303 6.96967Z"
									fill="currentColor"
								/>
							</svg>
						{:else}
							<svg
								width="20"
								height="20"
								viewBox="0 0 20 20"
								fill="none"
								xmlns="http://www.w3.org/2000/svg"
								class="text-red-500"
							>
								<path
									fill-rule="evenodd"
									clip-rule="evenodd"
									d="M10 18C14.4183 18 18 14.4183 18 10C18 5.58172 14.4183 2 10 2C5.58172 2 2 5.58172 2 10C2 14.4183 5.58172 18 10 18ZM8.70711 7.29289C8.31658 6.90237 7.68342 6.90237 7.29289 7.29289C6.90237 7.68342 6.90237 8.31658 7.29289 8.70711L8.58579 10L7.29289 11.2929C6.90237 11.6834 6.90237 12.3166 7.29289 12.7071C7.68342 13.0976 8.31658 13.0976 8.70711 12.7071L10 11.4142L11.2929 12.7071C11.6834 13.0976 12.3166 13.0976 12.7071 12.7071C13.0976 12.3166 13.0976 11.6834 12.7071 11.2929L11.4142 10L12.7071 8.70711C13.0976 8.31658 13.0976 7.68342 12.7071 7.29289C12.3166 6.90237 11.6834 6.90237 11.2929 7.29289L10 8.58579L8.70711 7.29289Z"
									fill="currentColor"
								/>
							</svg>
						{/if}
					{/if}
				</div>

				{#if isDropdownOpen}
					<!-- svelte-ignore a11y_click_events_have_key_events -->
					<div
						class="absolute top-full left-0 mt-1 w-64 max-h-60 overflow-y-auto bg-white border border-gray-200 rounded-lg shadow-lg z-30"
						use:clickOutside
						on:click={handleClickOutside}
					>
						{#each countryCodes as country}
							<!-- svelte-ignore a11y_click_events_have_key_events -->
							<!-- svelte-ignore a11y_no_static_element_interactions -->
							<div
								class="flex items-center gap-2 px-4 py-2 hover:bg-gray-100 cursor-pointer"
								class:bg-gray-50={country.code === selectedCountry.code}
								on:click={() => selectCountry(country)}
							>
								<span>{country.flag}</span>
								<span>{country.name}</span>
								<span class="text-gray-500 ml-auto">{country.dial_code}</span>
							</div>
						{/each}
					</div>
				{/if}
			</div>

			{#if errorMessage}
				<p class="text-red-500 text-sm mt-1">{errorMessage}</p>
			{/if}
		</div>
		<div class="grid grid-cols-1 mt-4">
			<label for="password" class="text-lg font-medium pb-2 text-[#111827]">Create password</label>
			<div class="relative flex items-center">
				<input
					class="bg-white p-3 pl-10 pr-12 border border-[#D1D5DB] rounded-lg w-full"
					id="password"
					type={showPassword ? 'text' : 'password'}
					bind:value={password}
					placeholder="Enter your password"
				/>
				<svg
					class="absolute left-3"
					width="18"
					height="18"
					viewBox="0 0 18 18"
					fill="none"
					xmlns="http://www.w3.org/2000/svg"
				>
					<path
						fill-rule="evenodd"
						clip-rule="evenodd"
						d="M15.9771 11.7904C18.6743 9.09318 18.6743 4.72013 15.9771 2.02291C13.2799 -0.674304 8.90682 -0.674304 6.20961 2.02291C4.41866 3.81385 3.8169 6.34366 4.40432 8.63112C4.49906 9.00004 4.41492 9.39902 4.14558 9.66835L0.433492 13.3804C0.115578 13.6984 -0.0405881 14.1435 0.00906183 14.5904L0.241128 16.679C0.26587 16.9017 0.365658 17.1093 0.524081 17.2677L0.732294 17.4759C0.890717 17.6343 1.09834 17.7341 1.32101 17.7589L3.4096 17.9909C3.85645 18.0406 4.30164 17.8844 4.61956 17.5665L5.32958 16.8565L3.58343 15.1294C3.28893 14.8382 3.28632 14.3633 3.5776 14.0688C3.86888 13.7743 4.34375 13.7717 4.63825 14.063L6.39026 15.7958L8.33192 13.8541C8.60126 13.5848 8.99996 13.5009 9.36888 13.5957C11.6563 14.1831 14.1861 13.5813 15.9771 11.7904ZM9.58579 5.58579C10.3668 4.80474 11.6332 4.80474 12.4142 5.58579C13.1953 6.36684 13.1953 7.63316 12.4142 8.41421C11.6332 9.19526 10.3668 9.19526 9.58579 8.41421C8.80474 7.63316 8.80474 6.36684 9.58579 5.58579Z"
						fill="#363062"
					/>
				</svg>
				<!-- Show/Hide Password Button -->
				<button
					type="button"
					class="absolute right-3 p-1"
					on:click={() => (showPassword = !showPassword)}
					aria-label={showPassword ? 'Hide password' : 'Show password'}
				>
					{#if showPassword}
						<!-- Hide Password Icon -->
						<svg
							width="24"
							height="24"
							viewBox="0 0 24 24"
							fill="none"
							stroke="currentColor"
							stroke-width="2"
							stroke-linecap="round"
							stroke-linejoin="round"
							class="text-gray-400 hover:text-gray-700"
						>
							<path
								d="M17.94 17.94A10.07 10.07 0 0 1 12 20c-7 0-11-8-11-8a18.45 18.45 0 0 1 5.06-5.94M9.9 4.24A9.12 9.12 0 0 1 12 4c7 0 11 8 11 8a18.5 18.5 0 0 1-2.16 3.19m-6.72-1.07a3 3 0 1 1-4.24-4.24"
							></path>
							<line x1="1" y1="1" x2="23" y2="23"></line>
						</svg>
					{:else}
						<!-- Show Password Icon -->
						<svg
							width="24"
							height="24"
							viewBox="0 0 24 24"
							fill="none"
							stroke="currentColor"
							stroke-width="2"
							stroke-linecap="round"
							stroke-linejoin="round"
							class="text-gray-400 hover:text-gray-700"
						>
							<path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"></path>
							<circle cx="12" cy="12" r="3"></circle>
						</svg>
					{/if}
				</button>
			</div>
		</div>

		<div class="grid grid-cols-1 mt-4">
			<label for="confirm-password" class="text-lg font-medium pb-2 text-[#111827]"
				>Confirm password</label
			>
			<div class="relative flex items-center">
				<input
					class="bg-white p-3 pl-10 pr-12 border border-[#D1D5DB] rounded-lg w-full"
					id="confirm-password"
					type={showConfirmPassword ? 'text' : 'password'}
					bind:value={confirmPassword}
					placeholder="Confirm your password"
				/>
				<svg
					class="absolute left-3"
					width="18"
					height="18"
					viewBox="0 0 18 18"
					fill="none"
					xmlns="http://www.w3.org/2000/svg"
				>
					<path
						fill-rule="evenodd"
						clip-rule="evenodd"
						d="M15.9771 11.7904C18.6743 9.09318 18.6743 4.72013 15.9771 2.02291C13.2799 -0.674304 8.90682 -0.674304 6.20961 2.02291C4.41866 3.81385 3.8169 6.34366 4.40432 8.63112C4.49906 9.00004 4.41492 9.39902 4.14558 9.66835L0.433492 13.3804C0.115578 13.6984 -0.0405881 14.1435 0.00906183 14.5904L0.241128 16.679C0.26587 16.9017 0.365658 17.1093 0.524081 17.2677L0.732294 17.4759C0.890717 17.6343 1.09834 17.7341 1.32101 17.7589L3.4096 17.9909C3.85645 18.0406 4.30164 17.8844 4.61956 17.5665L5.32958 16.8565L3.58343 15.1294C3.28893 14.8382 3.28632 14.3633 3.5776 14.0688C3.86888 13.7743 4.34375 13.7717 4.63825 14.063L6.39026 15.7958L8.33192 13.8541C8.60126 13.5848 8.99996 13.5009 9.36888 13.5957C11.6563 14.1831 14.1861 13.5813 15.9771 11.7904ZM9.58579 5.58579C10.3668 4.80474 11.6332 4.80474 12.4142 5.58579C13.1953 6.36684 13.1953 7.63316 12.4142 8.41421C11.6332 9.19526 10.3668 9.19526 9.58579 8.41421C8.80474 7.63316 8.80474 6.36684 9.58579 5.58579Z"
						fill="#363062"
					/>
				</svg>
				<!-- Show/Hide Confirm Password Button -->
				<button
					type="button"
					class="absolute right-3 p-1"
					on:click={() => (showConfirmPassword = !showConfirmPassword)}
					aria-label={showConfirmPassword ? 'Hide password' : 'Show password'}
				>
					{#if showConfirmPassword}
						<!-- Hide Password Icon -->
						<svg
							width="24"
							height="24"
							viewBox="0 0 24 24"
							fill="none"
							stroke="currentColor"
							stroke-width="2"
							stroke-linecap="round"
							stroke-linejoin="round"
							class="text-gray-400 hover:text-gray-700"
						>
							<path
								d="M17.94 17.94A10.07 10.07 0 0 1 12 20c-7 0-11-8-11-8a18.45 18.45 0 0 1 5.06-5.94M9.9 4.24A9.12 9.12 0 0 1 12 4c7 0 11 8 11 8a18.5 18.5 0 0 1-2.16 3.19m-6.72-1.07a3 3 0 1 1-4.24-4.24"
							></path>
							<line x1="1" y1="1" x2="23" y2="23"></line>
						</svg>
					{:else}
						<!-- Show Password Icon -->
						<svg
							width="24"
							height="24"
							viewBox="0 0 24 24"
							fill="none"
							stroke="currentColor"
							stroke-width="2"
							stroke-linecap="round"
							stroke-linejoin="round"
							class="text-gray-400 hover:text-gray-700"
						>
							<path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"></path>
							<circle cx="12" cy="12" r="3"></circle>
						</svg>
					{/if}
				</button>
			</div>
		</div>
		<div class="text-center">
			<button
				on:click={goToAuthentication}
				type="submit"
				class="bg-[#363062] py-3 text-white w-full font-medium rounded-lg mt-6">Send</button
			>
		</div>
	</div>
</div>

<style>
	input[type='tel']::-webkit-outer-spin-button,
	input[type='tel']::-webkit-inner-spin-button {
		-webkit-appearance: none;
		margin: 0;
	}

	input[type='tel'] {
		-moz-appearance: textfield;
	}
</style>

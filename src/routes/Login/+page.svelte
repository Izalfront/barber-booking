<script lang="ts">
	import bg from './img/bg-login.svg';
	import people from './img/hdprofile.png';
	let email = '';
	let password = '';

	function handleLogin() {
		console.log('Login with', email, password);
	}

	function goToRegister() {
		window.location.href = '/register';
	}

	function goToForgotPassword() {
		window.location.href = '/forgot-password';
	}

	function goToHome() {
		window.location.href = '/home';
	}
</script>

<main class="w-full max-w-[500px] mx-auto text-base overflow-x-hidden h-screen">
	<div class="bg-[#F99417] relative">
		<img class="absolute w-full top-8" src={people} alt="" />
		<img class="w-full" src={bg} alt="" />
	</div>
	<div class="bg-white rounded-t-3xl -translate-y-8 p-6">
		<h2 class="text-3xl font-bold text-[#363062]">Welcome back 👋</h2>
		<p class="text-lg font-normal text-[#6B7280] pt-2">
			Please enter your login information below to access your account
		</p>

		<form class="mt-4" on:submit|preventDefault={handleLogin}>
			<div class="grid grid-cols-1">
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

			<div class="mt-4 grid grid-cols-1">
				<label for="password" class="text-lg font-medium pb-2 text-[#111827]">Password</label>
				<div class="relative flex items-center">
					<input
						class="bg-white p-3 pl-10 border border-[#D1D5DB] rounded-lg w-full"
						id="password"
						type="password"
						placeholder="Password"
						bind:value={password}
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
				</div>
			</div>
			<div class="text-end">
				<button class="text-[#363062] font-semibold mt-4" on:click={goToForgotPassword}
					>Forgot password?</button
				>
			</div>
			<div class="text-center">
				<button
					type="submit"
					class="bg-[#363062] py-3 text-white w-[41vh] font-medium rounded-lg mt-6"
					on:click={goToHome}>Login</button
				>
			</div>
		</form>
		<div class="text-center mt-4">
			<button class="text-gray-500 font-bold" on:click={goToRegister}
				>Don't have an account? <span class="text-[#363062] font-bold">Register</span></button
			>
		</div>
	</div>
</main>

<script>
	let email = '';
	let password = '';

	function handleLogin() {
		// Logika login sederhana untuk demo
		console.log('Login with', email, password);
	}

	function goToRegister() {
		window.location.href = '/Register';
	}
</script>

<main class="w-full max-w-[500px] mx-auto text-base overflow-x-hidden h-screen">
	<h2>Login</h2>
	<form on:submit|preventDefault={handleLogin}>
		<label for="email">Email:</label>
		<input id="email" type="email" bind:value={email} />

		<label for="password">Password:</label>
		<input id="password" type="password" bind:value={password} />

		<button type="submit">Login</button>
	</form>

	<button on:click={goToRegister}>Don't have an account? Register</button>
</main>

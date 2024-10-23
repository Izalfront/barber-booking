<script>
	let email = '';
	let password = '';
	let confirmPassword = '';

	function handleRegister() {
		if (password === confirmPassword) {
			// Logika register sederhana untuk demo
			console.log('Register with', email, password);
		} else {
			alert('Passwords do not match');
		}
	}
</script>

<main>
	<h2>Register</h2>
	<form on:submit|preventDefault={handleRegister}>
		<label for="email">Email:</label>
		<input id="email" type="email" bind:value={email} />

		<label for="password">Password:</label>
		<input id="password" type="password" bind:value={password} />

		<label for="confirmPassword">Confirm Password:</label>
		<input id="confirmPassword" type="password" bind:value={confirmPassword} />

		<button type="submit">Register</button>
	</form>
</main>

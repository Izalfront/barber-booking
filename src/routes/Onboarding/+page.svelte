<script lang="ts">
	let currentSlide = 0;
	const slides = [
		{
			id: 1,
			title: 'Welcome to Barber App',
			description: 'Your perfect barber at your fingertips.'
		},
		{ id: 2, title: 'Looking for barbers?', description: 'Find professional barbers easily.' },
		{
			id: 3,
			title: 'Everything you need.',
			description: 'Book, chat, and manage your appointments.'
		}
	];

	function nextSlide() {
		if (currentSlide < slides.length - 1) {
			currentSlide++;
		} else {
			// Navigasi ke halaman login
			window.location.href = '/Login';
		}
	}
</script>

<main>
	hello
	<div>
		<h2>{slides[currentSlide].title}</h2>
		<p>{slides[currentSlide].description}</p>
	</div>
	<button on:click={nextSlide}>
		{#if currentSlide < slides.length - 1}
			Next
		{:else}
			Go to Login
		{/if}
	</button>
</main>

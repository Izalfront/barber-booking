<script>
	import '../app.css';
	import { Router, Route } from 'svelte-routing';
	import home from './home/+page.svelte';
	import barberdetail from './detail-barber/+page.svelte';
</script>

<div class="app">
	<main>
		<slot />
	</main>
</div>

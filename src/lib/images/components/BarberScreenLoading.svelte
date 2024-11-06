<script>
	import { blur } from 'svelte/transition';

	let { loading } = $props();
</script>

{#if loading}
	<div
		style="position: fixed;inset: 0;background-color: #363062;display: flex;align-items: center;justify-content: center;z-index: 10;column-gap: 8px;"
		out:blur={{ duration: 700, delay: 100 }}
	>
		<img
			class="animate-loading"
			src="./gobar.svg"
			alt="Loading..."
			style="width: 80px; height: auto"
		/>
	</div>
{/if}

<style>
	.animate-loading {
		animation: loading 1.5s linear infinite;
	}
	@keyframes loading {
		0% {
			opacity: 0.15;
		}
		50% {
			opacity: 1;
		}
		100% {
			opacity: 0.15;
		}
	}
</style>

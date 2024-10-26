<script lang="ts">
	function goToFindBarber() {
		window.location.href = '/find-barber';
	}
</script>

<!-- svelte-ignore a11y_missing_attribute -->
<div class="my-6">
	<h1 class="text-xl font-semibold mb-2">Find a barber nearby</h1>
	<div class="relative overflow-hidden">
		<iframe
			class="w-96 h-60 rounded-xl mb-6"
			src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3982.5885977056646!2d114.79679321146358!3d-3.4497489418055594!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2de683bc639c0bb3%3A0x633e3e112fe67a3e!2sBebek%20sinjaya!5e0!3m2!1sid!2sid!4v1729769016891!5m2!1sid!2sid"
			width="600"
			height="450"
		></iframe>
		<div class="flex justify-end">
			<button
				on:click={goToFindBarber}
				class="flex gap-x-2 text-lg items-center bg-[#363062] py-2 px-6 rounded-xl text-white"
				>Find now <svg
					width="20"
					height="20"
					viewBox="0 0 20 20"
					fill="none"
					xmlns="http://www.w3.org/2000/svg"
				>
					<path
						d="M9.58317 17.5001C13.9554 17.5001 17.4998 13.9557 17.4998 9.58341C17.4998 5.21116 13.9554 1.66675 9.58317 1.66675C5.21092 1.66675 1.6665 5.21116 1.6665 9.58341C1.6665 13.9557 5.21092 17.5001 9.58317 17.5001Z"
						stroke="#fff"
						stroke-width="1.5"
						stroke-linecap="round"
						stroke-linejoin="round"
					/>
					<path
						d="M18.3332 18.3334L16.6665 16.6667"
						stroke="#fff"
						stroke-width="1.5"
						stroke-linecap="round"
						stroke-linejoin="round"
					/>
				</svg></button
			>
		</div>
	</div>
</div>

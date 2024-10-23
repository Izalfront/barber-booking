<script lang="ts">
	let code = ['', '', '', ''];

	function handleInputChange(index: number, event: Event) {
		const target = event.target as HTMLInputElement;
		code[index] = target.value;

		if (target.value.length === 1 && index < code.length - 1) {
			const nextInput = document.getElementById(`input-${index + 1}`);
			nextInput?.focus();
		}
	}

	function handleKeyDown(index: number, event: KeyboardEvent) {
		if (event.key === 'Backspace' && code[index] === '' && index > 0) {
			const prevInput = document.getElementById(`input-${index - 1}`);
			prevInput?.focus();
		}
	}

	function goToAuthentication() {
		// console.log(code.join(''));
		window.location.href = '/Login';
	}
</script>

<div class="w-full max-w-[500px] mx-auto text-base overflow-x-hidden h-screen">
	<div class="mt-48 mx-8">
		<h1 class="text-3xl font-[700] text-[#363062]">Authentication</h1>
		<p class="text-xl mt-2 text-[#6B7280]">
			Please enter the authentication code that we have sent to your email
		</p>

		<div class="grid grid-cols-4 gap-4 mt-12">
			{#each code as _, index}
				<input
					type="text"
					id={`input-${index}`}
					maxlength="1"
					bind:value={code[index]}
					on:input={(event) => handleInputChange(index, event)}
					on:keydown={(event) => handleKeyDown(index, event)}
					class="w-full h-[70px] text-2xl text-center border border-[#D1D5DB] rounded-xl focus:outline-none focus:ring focus:border-[#9CA3AF]"
				/>
			{/each}
		</div>
		<div class="text-center">
			<button
				type="submit"
				class="bg-[#363062] py-3 text-white w-full font-medium rounded-lg mt-6"
				on:click={goToAuthentication}>Send</button
			>
		</div>
	</div>
</div>

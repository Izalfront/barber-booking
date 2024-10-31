<script lang="ts">
	import gobar from './img/logo-gobar.png';
	import SwitchContent from './SwitchContent.svelte';
</script>

<div class="w-full max-w-[500px] mx-auto text-base overflow-x-hidden h-screen">
	<div class="flex justify-between items-center bg-[#363062] p-6">
		<h1 class="text-white font-semibold text-lg">Booking</h1>
		<img class="w-auto h-8" src={gobar} alt="" />
	</div>
	<div class="p-6">
		<SwitchContent />
	</div>
</div>

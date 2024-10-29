<script lang="ts">
	import OpeningHours from './about child/OpeningHours.svelte';
	import OurTeam from './about child/OurTeam.svelte';
</script>

<div class="p-6">
	<p class="text-slate-500 text-lg">
		At Masterpiece Barbershop, our dedicated team of skilled barbers are true artists in their
		craft, transforming your hair
	</p>
	<div>
		<OpeningHours />
	</div>
	<div>
		<OurTeam />
	</div>
	<div>
		<button class="w-full h-14 rounded-xl text-white font-semibold bg-[#363062] mt-4 tracking-wide"
			>Booking Now</button
		>
	</div>
</div>

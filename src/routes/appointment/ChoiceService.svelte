<script lang="ts">
	import choice from './img/choice.png';
	import choice1 from './img/choice1.png';
	import choice2 from './img/choice2.png';
	import centang from './img/centang.svg';

	let choices = [
		{
			id: 1,
			title: 'Basic haircut',
			salary: '$20',
			img: choice
		},
		{
			id: 2,
			title: 'Kisd haricut',
			salary: '$15',
			img: choice1
		},
		{
			id: 3,
			title: 'Hair coloring',
			salary: '$30',
			img: choice2
		}
	];
</script>

<div>
	<h1 class="font-semibold text-lg leading-tight my-2">Choose Service</h1>
	<div class="mt-3 flex justify-between gap-6">
		{#each choices as data}
			<div class="flex flex-col items-center">
				<div class="size-14"><img class="h-full w-full" src={data.img} alt="" /></div>
				<div class="text-center mt-1">
					<h1 class="text-lg font-semibold">{data.title}</h1>
					<p class="text-slate-500 font-medium">{data.salary}</p>
				</div>
			</div>
		{/each}
	</div>
</div>

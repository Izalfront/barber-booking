<!-- Tags.svelte -->
<script lang="ts">
	export let tags: Array<{
		text: string;
		active?: boolean;
		highlighted?: boolean;
	}> = [];

	function handleTagClick(index: number) {
		tags = tags.map((tag, i) => ({
			...tag,
			active: i === index ? !tag.active : tag.active
		}));
	}
</script>

<div class="flex flex-wrap gap-6 border py-8 rounded-xl">
	{#each tags as tag, index}
		<button
			class="px-4 py-2 rounded-full text-sm transition-colors duration-200
          {tag.highlighted ? 'bg-[#363062] text-white' : 'bg-gray-100 text-gray-600'} 
          {tag.active ? 'text-white bg-[#363061]' : ''}"
			on:click={() => handleTagClick(index)}
		>
			{tag.text}
		</button>
	{/each}
</div>

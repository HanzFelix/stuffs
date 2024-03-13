<script>
	let colors = ['bg-yellow-700', 'bg-purple-800', 'bg-blue-800', 'bg-teal-700'];
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section class="p-4">
	<div class="flex gap-4 items-center">
		{#each colors as color, i}
			<div class="bg-gray-300 rounded-lg overflow-hidden">
				<div class="size-24 {colors[i]} rounded-br-2xl"></div>
				<input
					type="text"
					class="bg-transparent text-center text-lg py-1 w-full"
					size="1"
					value="3"
				/>
			</div>
			{#if i < colors.length - 1}
				<div class="flex flex-col">
					<button class="{colors[i]} text-white">⩤</button>
					<input type="text" size="1" value="1:3" class="text-center" />
					<button class="{colors[i + 1]} text-white">⩥</button>
				</div>
			{/if}
		{/each}
	</div>
</section>

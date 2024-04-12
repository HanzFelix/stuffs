<script>
	let colors = ['bg-yellow-700', 'bg-purple-800', 'bg-blue-800', 'bg-teal-700'];
	//colors = ['bg-blue-800', 'bg-blue-800', 'bg-blue-800', 'bg-blue-800'];
	let ratio = [
		[1, 3],
		[1, 3],
		[1, 3],
		[1, 3]
	];
	let have = [6, 6, 6, 6];

	function convert(id, from) {
		have[id] = Number(have[id]) + from * ratio[id][0];
		have[id + 1] = Number(have[id + 1]) + from * -ratio[id][1];
	}
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section class="p-4">
	<div class="flex gap-4 items-center">
		<button class="text-white bg-black px-2 py-1">R</button>
		{#each colors as color, i}
			<div class="bg-gray-200 rounded-lg overflow-hidden">
				<div class="size-24 {colors[i]} rounded-br-2xl">a</div>
				<input
					type="text"
					class="bg-transparent text-center text-lg py-1 rounded-b-lg w-full {have[i] < 0
						? 'text-red-700'
						: ''}"
					size="1"
					bind:value={have[i]}
				/>
			</div>
			{#if i < colors.length - 1}
				<div class="flex flex-col rounded-md overflow-hidden">
					<button class="{colors[i]} text-white" on:click={() => convert(i, 1)}>⩤</button>
					<!--TODO: bind <input> to ratio[][]-->
					<input
						type="text"
						size="1"
						value={ratio[i].join(':')}
						class="text-center bg-gray-200"
						on:input={(e) => (ratio[i] = e.target.value.split(':').map(Number))}
					/>
					<button class="{colors[i + 1]} text-white" on:click={() => convert(i, -1)}>⩥</button>
				</div>
			{/if}
		{/each}
	</div>
</section>

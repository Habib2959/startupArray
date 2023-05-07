<script>
	// @ts-ignore
	import { flip } from 'svelte/animate';
	import { dndzone } from 'svelte-dnd-action';
	// @ts-ignore
	export let items;
	const flipDurationMs = 300;
	function handleDndConsider(e) {
		items = e.detail.items;
		console.log(items);
	}
	function handleDndFinalize(e) {
		items = e.detail.items;
	}
</script>

<div class="coloum">
	<section
		use:dndzone={{ items, flipDurationMs }}
		on:consider={handleDndConsider}
		on:finalize={handleDndFinalize}
	>
		{#each items as item (item.id)}
			<div class="task" animate:flip={{ duration: flipDurationMs }}>{item.name}</div>
		{/each}
	</section>
</div>

<style>
	.coloum {
		border: 2px solid #ccc;
		width: 200px;
		min-height: 500px;
		height: 100%;
		overflow-y: scroll;
		margin-top: 20px;
	}
	section {
		width: 100%;
		padding: 0.3em;
	}
	.task {
		padding: 5px;
		border: 1px solid #ccc;
		border-radius: 5px;
		margin: 5px;
	}
</style>

<script>
	// @ts-ignore
	import Coloum from './Coloum.svelte';

	let items = [
		{ id: 1, name: 'item1' },
		{ id: 2, name: 'item2' },
		{ id: 3, name: 'item3' },
		{ id: 4, name: 'item4' }
	];

	let taskTitle = '';
	const createColum = () => {};
	const handleTask = () => {
		let newItem = { id: items.length + 1, name: taskTitle };
		items.push(newItem);
		items = items;
		taskTitle = '';
	};
</script>

<div>
	<button on:click={createColum}>Add Coloum</button>
	<form on:submit|preventDefault={handleTask}>
		<input type="text" placeholder="Task title" required bind:value={taskTitle} />
		<button type="submit">Add Task</button>
	</form>
</div>

<Coloum {items} />

<style>
	input {
		padding: 3px;
	}
</style>

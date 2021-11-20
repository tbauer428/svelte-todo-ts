<script lang="ts">
	let todos: string[] = ['click me to remove'];

	let todo: string = '';

	const addTodo = () => {
		todos = [...todos, todo]
		todo = '';
	}

	const removeTodo = (index: number) => {
		todos.splice(index, 1)
		todos = todos;
	}
</script>

<main>
	<h1>todos</h1>
	<form on:submit|preventDefault={addTodo}>
    	<input bind:value={todo} placeholder='new todo'>
		<button>ADD</button>
	</form>
	
	{#each todos as todo, index}
		<p on:click={() => removeTodo(index)}>{todo}</p>
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
<script lang="ts">
	let todos: string[] = ['click me to remove'];

	let todo: string = '';

	const addTodo = () => {
		todos = [...todos, todo]
		todo = '';
	}

	const removeTodo = (i: number) => {
		todos.splice(i, 1)
		todos = todos;
	}
</script>

<main>
	<h1>todos</h1>
	<form on:submit|preventDefault={addTodo}>
    	<input bind:value={todo} placeholder='new todo'>
		<button>ADD</button>
	</form>
	
	{#each todos as todo, i}
		<p on:click={() => removeTodo(i)}>{todo}</p>
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
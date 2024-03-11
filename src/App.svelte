<script>
	import { todos } from "./stores";
	import AddTodo from "./components/AddTodo.svelte";
	import Todo from "./components/Todo.svelte";
	import Toast from "./components/Toast.svelte";
	

	if (localStorage.getItem("todos")) {
		todos.local(JSON.parse(localStorage.getItem("todos")))
	}

	$: localStorage.setItem("todos", JSON.stringify($todos));
	
</script>

<div class="container">
	<h1 class="display">TODO App</h1>
	<AddTodo />
	
	{#each $todos as item}
		<Todo {item} />
	{/each}
	<Toast />
</div>

<style>
</style>

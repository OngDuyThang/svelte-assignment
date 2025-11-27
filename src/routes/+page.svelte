<script lang="ts">
	import { onMount } from 'svelte';
	import FilterButton from '../components/filter-button.svelte';
	import TaskList from '../components/task-list.svelte';
	import TodoForm from '../components/todo-form.svelte';
	import { LOCAL_STORAGE_KEY } from '../utils/constants';
	import type { Filter, Task } from '../utils/types';

	let tasks = $state<Task[]>([]);
	let currentFilter = $state<Filter>('all');
	let isFirstMount = true;

	onMount(() => {
		tasks = JSON.parse(localStorage.getItem(LOCAL_STORAGE_KEY) || '[]') || [];
		isFirstMount = false;
	});
	$effect(() => {
		if (!isFirstMount) {
			localStorage.setItem(LOCAL_STORAGE_KEY, JSON.stringify(tasks));
		}
	});

	let filteredTasks = $derived.by(() => {
		switch (currentFilter) {
			case 'all': {
				return tasks;
			}
			case 'todo': {
				return tasks.filter((task) => !task.done);
			}
			case 'done': {
				return tasks.filter((task) => task.done);
			}
		}
	});
	let totalDone = $derived(tasks.reduce((total, task) => total + Number(task.done), 0));

	const addTask = (newTask: string) => {
		tasks.push({
			id: crypto.randomUUID(),
			title: newTask,
			done: false
		});
	};

	const toggleDone = (task: Task) => {
		task.done = !task.done;
	};

	const removeTask = (id: string) => {
		const index = tasks.findIndex((task) => task.id === id);
		tasks.splice(index, 1);
	};
</script>

{#snippet filterButton(buttonType: Filter)}
	<FilterButton
		{buttonType}
		{currentFilter}
		changeFilter={(filter: Filter) => {
			currentFilter = filter;
		}}
	/>
{/snippet}

<main>
	<h1>Todo App</h1>
	<TodoForm {addTask} />
	<p>
		{#if tasks.length}
			{totalDone} / {tasks.length} tasks completed
		{:else}
			Add a task to get started.
		{/if}
	</p>
	{#if tasks.length}
		<div class="button-container">
			<span>Filter:</span>
			{@render filterButton('all')}
			{@render filterButton('todo')}
			{@render filterButton('done')}
		</div>
	{/if}
	<TaskList tasks={filteredTasks} {toggleDone} {removeTask} />
</main>

<style>
	main {
		margin: 1rem auto;
		max-width: 800px;
	}

	.button-container {
		display: flex;
		align-items: center;
		justify-content: end;
		margin-bottom: 1rem;
		gap: 0.5rem;
	}
</style>

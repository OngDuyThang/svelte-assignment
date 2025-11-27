<script lang="ts">
	interface IProps {
		addTask: (newTask: string) => void;
	}

	let newTask = $state('');
	let { addTask }: IProps = $props();

	const handleSubmit = (e: SubmitEvent) => {
		e.preventDefault();
		addTask(newTask);
		newTask = '';
	};
</script>

<form onsubmit={handleSubmit}>
	<input name="newTask" id="task-input" bind:value={newTask} placeholder="Enter your task" />
	<button type="submit">Add</button>
</form>

<style>
	form {
		margin-bottom: 1rem;
	}
</style>

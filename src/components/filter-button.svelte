<script lang="ts">
	import type { Filter } from '../utils/types';

	interface IProps {
		buttonType: Filter;
		currentFilter: Filter;
		changeFilter: (filter: Filter) => void;
	}

	let { buttonType, currentFilter, changeFilter }: IProps = $props();
</script>

<button
	onclick={() => changeFilter(buttonType)}
	class:contrast={currentFilter === buttonType}
	class="secondary filter-button"
>
	{buttonType.split('')[0].toUpperCase() + buttonType.slice(1)}
</button>

<style>
	.filter-button {
		text-transform: capitalize;
		padding: 0.3rem 1rem;
		border-radius: 0.5rem;
	}
</style>

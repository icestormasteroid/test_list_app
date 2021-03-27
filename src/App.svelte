<script>
	import Todos from './Todos.svelte'
</script>

<svelte:head>
  <script src="https://use.fontawesome.com/releases/v5.3.1/js/all.js"></script>
</svelte:head>

<main>
	<h1>My Basic To-Do List!</h1>
	<Todos />
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
<script>
	import Modal from "./components/modal.svelte";

	import Box from "./pages/box.svelte";
</script>

<style>
	:global(body) {
		background-color: #144552;
	}
	main {
		text-align: center;
		padding: 1em;
		max-width: 400px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>

<Box />
<main />

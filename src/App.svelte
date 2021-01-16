<script>
	import Router from "svelte-spa-router";
	import Nav from "./components/nav.svelte";

	import Box from "./pages/box.svelte";
	import Filter from "./pages/filter.svelte";
	import Gradient from "./pages/gradient.svelte";
	import Home from "./pages/home.svelte";
	import Text from "./pages/text.svelte";

	const routes = {
		"/box": Box,

		"/text": Text,

		"/gradient": Gradient,

		"/filter": Filter,

		"/": Home,
	};
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

<Router {routes} />
<main />

<svelte:head>
	<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.1/dist/css/bootstrap.min.css">
</svelte:head>

<script>
	import { Route, Router, Link } from "svelte-navigator"

	import Homepage from "./Homepage.svelte"
	import Games from "./Games.svelte"
	import GamePage from "./GamePage.svelte"
</script>

<style>
	.background {
		background-image: url(/resources/bg.png);
		background-position: bottom;
		background-repeat: no-repeat;
		background-size: cover;
		height: 100vh;
		width: 100%;
		position: absolute;
		z-index: -1;
	}

	.blur {
		background: rgba(255, 255, 255, 0.2);
		backdrop-filter: blur(8px);
		height: 100vh;
		width: 100%;
	}
</style>

<div class="background">
	<div class="blur"></div>
</div>

<Router>
	<!-- Homepage Route -->
	<Route path="/">
		<Homepage />
	</Route>

	<!-- Route to List of Games -->
	<Route path="games">
		<Games />
	</Route>

	<!-- Route to the games About page -->
	<Route path="games/:id" let:params>
		<GamePage gameTitle={params.id} />
	</Route>

	<!-- Route to about Cooky Studios about page -->
	<Route path="about">
		<!-- TBD -->
	</Route>
</Router>
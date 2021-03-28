<script lang="ts">
	import 'bulma/css/bulma.css';

	import { Button } from 'svelma'
import Footer from './Footer.svelte';
import Header from './Header.svelte';

</script>

<svelte:head>
	<title>Chris Vaksdal</title>
	<html lang="en" />
</svelte:head>

<main>
	<Header></Header>
	<Button>I am a Button</Button>
	<Footer></Footer>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
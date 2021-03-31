<script lang="ts">

	import router from 'page'
	import Home from '../routes/Home.svelte'
	import Blog from '../routes/Blog.svelte'

	let page
  	let params
	
	router('/', () => (page = Home))
	router('/blog', () => (page = Blog))

	router.start()

</script>

<svelte:component this="{page}" params="{params}" />

<svelte:head>
	<title>Chris Vaksdal</title>
	<html lang="en" />
</svelte:head>

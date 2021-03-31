<script lang="ts">

	import router from 'page'
	import Home from '../routes/Home.svelte'
	import Blog from '../routes/Blog.svelte'
	import Post from '../routes/Post.svelte'

	import Footer from './Footer.svelte'

	let page
  	let params
	
	router('/', () => (page = Home))
	router('/blog', () => (page = Blog))
	router(
		'/blog/:id',
		(ctx, next) => 
			{
				params = ctx.params
				next()
			},
		() => (page = Post)
  	)

	router.start()

</script>

<svelte:head>
	<title>Chris Vaksdal</title>
	<html lang="en" />
</svelte:head>

<svelte:component this="{page}" params="{params}" />

<Footer />

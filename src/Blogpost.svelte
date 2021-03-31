<script lang="ts">
	import 'bulma/css/bulma.css';

	import { onMount } from 'svelte';

	let blogPostURL: string = '../blog-posts/test-post';

	function calculateBlogPostURL(){
		let path: string = window.location.href
		blogPostURL = path.substring(path.lastIndexOf('/') + 1)
	}

	onMount(() => calculateBlogPostURL())

	/**
	 * Fetches a markdown blog post using the local API.
	 * @param url
	 */
	const fetchPost = async (url: string): Promise<string> => {
		const response: Response = await fetch(url)
		const data: string  = await response.text().then()
		return data
	}

</script>

<main>

    <h1>Gogogadget</h1>

	{#await fetchPost(blogPostURL)}
	<span class="loading">Loading post...</span>
	{:then blog}
		Data:<br>
		<section class="blog-post">
			{@html blog}
		</section>
		
		<br>End data.
	{:catch error}
		<p>An error occurred!</p>
		{error}
	{/await}
	
</main>

<style>
    :global .blog-post img{
		width: 10%;
	}
</style>
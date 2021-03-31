<script lang="ts">
	import 'bulma/css/bulma.css'

	import { onMount } from 'svelte'

	export let blogPostURL: string

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
		<section class="blog-post">
			{@html blog}
		</section>
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
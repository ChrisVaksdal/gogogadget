<script lang="ts">

	import 'bulma/css/bulma.css'

	import { onMount } from 'svelte'
    import { fade } from 'svelte/transition'

	//TODO:import Spinner from 'svelte-spinkit';	// Make this work.

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
	
	<div class="container">

		<h1 class="title">Gogogadget</h1>
		
		{#await fetchPost(blogPostURL)}
			<h1 class="title has-text-centered subtitle">Loading post...</h1>
			<!-- <Spinner name="rotating-plane" color="blue" /> -->
		{:then blog}
			<section in:fade class="blog-post">
				{@html blog}
			</section>
		{:catch error}
			<p>An error occurred!</p>
			{error}
		{/await}

	</div>

</main>

<style>

	.container{
		padding: 20px 0px;
	}

	/* Custom CSS for fetched content: */

	/* Special for phones */
	@media (max-width: 599px) {
		.blog-post{
			padding-left: 15px;
			padding-right: 15px;
		}
  	}

  	/* Table of Contents */
	.blog-post :global(div.toc){
		font-size: 1rem;
		list-style-type: circle !important;
		margin: auto;
		padding-bottom: 15px;
	}

	.blog-post :global(.toc ul li){
		font-size: 0.8rem;
		list-style-type: circle !important;
		border-style: solid rgba(14, 25, 80, 0.3) 1px;
	}

	/* Images */
    .blog-post :global(img){
		max-height: 30rem;
		box-shadow: 0 5px 20px rgba(14, 25, 80, 0.3);
		border-radius: 2%;
		display: block;
		margin-left: auto;
		margin-right: auto;
		margin-top: 30px;
		margin-bottom: 40px;
	}

	/* Headings */
	.blog-post :global(h1) {
		font-size: 4rem;
		padding: 10px;
	}

	.blog-post :global(h2) {
		font-size: 2rem;
		padding-bottom: 8px;
	}

	.blog-post :global(h3) {
		font-size: 1.2rem;
		padding-bottom: 4px;
		font-weight: 600;
	}

	/* Text */
	.blog-post :global(p) {
		font-size: 1rem;
		padding: 5px;
	}

	/* Tables */
	.blog-post :global(table) {
		font-family: Arial, Helvetica, sans-serif;
		border-collapse: collapse;
		width: 60%;
		margin: auto;
		padding: 100px;
		box-shadow: 0 5px 20px rgba(14, 25, 80, 0.3);
	}

	.blog-post :global(th) {
		padding-top: 6px;
		padding-bottom: 6px;
		text-align: center;
		background-color: rgb(31, 44, 108);
		color: white;
	}

	.blog-post :global(td, th) {
		border: 1px solid #ddd;
  		padding: 8px;
	}


	.blog-post :global(tr:hover) {
		background-color: #ddd;
	}

	.blog-post :global(tr:nth-child(even)) {
		background-color: #f2f2f2;
	}

	.blog-post :global(tr:hover) {
		background-color: #ddd;
	}

	/* Lists */
	.blog-post :global(ul) {
		list-style-position: inside;
		list-style-type: square;
	}

	.blog-post :global(ul li) {
		list-style-type: square;
	}

</style>
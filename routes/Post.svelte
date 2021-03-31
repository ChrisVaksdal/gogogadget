<script lang="ts">

    import Blogpost from '../src/Blogpost.svelte'

    export let params: {id: string}
    let blogPostURL = `../blog-posts/${params.id}`

</script>

<svelte:head>
	<title>Gogogadget</title>
</svelte:head>

<main>
    <h1>Blog Post</h1>
    <Blogpost blogPostURL={blogPostURL}></Blogpost>
</main>
<script lang="ts">

    import 'bulma/css/bulma.css'

    import ToTopButton from './ToTopButton.svelte';
    import Blogpost from '../src/Blogpost.svelte'
    import Icon from 'fa-svelte'

    import { faArrowLeft } from '@fortawesome/free-solid-svg-icons/faArrowLeft'

    const icon = faArrowLeft

    export let params: {id: string}
    const blogPostURL = `../blog-posts/posts/${params.id}`

</script>

<svelte:head>
	<title>Gogogadget</title>
</svelte:head>

<main>
    <a href="/blog" id="backButton">
        <Icon icon={icon} />
    </a>

    <ToTopButton />
    <Blogpost blogPostURL={blogPostURL}></Blogpost>
</main>

<style>

    #backButton{
		text-align: center;
		height: 50px;
		width: 50px;
		position: fixed;
		top: 20px;
		left: 30px;
		z-index: 99;
		border: none;
		outline: none;
		background-color: rgba(31, 44, 108, 0.65);
		color: white;
		cursor: pointer;
		border-radius: 50%;
		font-size: 2rem;
		box-shadow: 0 5px 20px rgba(14, 25, 80, 0.3);
	}

	@media (max-width: 599px) {
		#backButton{
			left: auto;
			right: 30px;
		}
  	}

</style>
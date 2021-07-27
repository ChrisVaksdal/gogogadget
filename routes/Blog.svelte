<script lang="ts">

    import 'bulma/css/bulma.css'

    import Navbar from '../src/Navbar.svelte'
    import ToTopButton from './ToTopButton.svelte';

    import { fade } from 'svelte/transition'

    let navItems: Array<{label: string, href: string, id: string}> = [
        { label: "Posts", href: "", id: "#posts-section"},
        { label: "About the blog", href: "", id: "#about-section"},
        { label: "About me", href: "/#", id: ""},
    ]

    interface postsJSON {
        "number": number
        "titles": Array<string>
    }

    async function getPostTitles(){
        const res = await fetch('../blog-posts/all_titles');
		const posts: postsJSON = await res.json()
        return posts
    }

    function getPostURL(postTitle: string){
        return `/blog/${postTitle}`
    }

    function getHeaderURL(postTitle: string){
        return `/blog-posts/header-image/${postTitle}`
    }

    function formatPostTitle(postTitle: string){
        let title: string = postTitle
        title = postTitle.replace("_", " ")                                             // Remove underscores
        title = title.replace(/(^\w{1})|(\s+\w{1})/g, letter => letter.toUpperCase());  // Capitalize beginning of every word.
        return title
    }

    function getPostType(postTitle: string){
        return "general"
    }


</script>

<svelte:head>
	<title>Gogogadget</title>
</svelte:head>

<main>

    <ToTopButton />

    <Navbar navItems = {navItems}/>

    <section class="container">

        <div class="columns is-multiline" id="posts-section">

            <div class="column is-12">
                <h1 class="title has-text-centered section-title">Check out my work!</h1>
            </div>
            
            {#await getPostTitles()}
                <div class="column is-12">
                    <h1 class="title has-text-centered subtitle">Loading posts...</h1>
                </div>
            {:then posts}
                {#each posts["titles"] as post}
                    <div class="column is-3" in:fade>
                        <a href={getPostURL(post)}>
                            <figure class="image is-2by1 blogpost" style="background-image: url({getHeaderURL(post)});">
                                <figcaption 
                                    class="tag is-medium"
                                    class:is-success="{getPostType(post) === 'software'}"
                                    class:is-danger="{getPostType(post) === 'electronics'}"
                                    class:is-warning="{getPostType(post) === 'idea'}"
                                    class:is-primary="{getPostType(post) === 'general'}"
                                >
                                    {formatPostTitle(post)}
                                </figcaption>
                            </figure>
                        </a>
                    </div>
                {/each}
            {:catch error}
                <div class="column is-12">
                    <h1 class="title has-text-centered subtitle">An error has ocurred.</h1>
                    <h1 class="title has-text-centered subtitle">Please reload the page or try again later.</h1>
                </div>
            {/await}

        </div>

    </section>

    <section class="container" id="about-section">

        <div class="columns is-multiline">

            <div class="column is-12">
                <h1 class="title has-text-centered section-title">About The Blog</h1>
            </div>
            
            <div class="column is-12">
                <h2 class="subtitle has-text-centered">
                    Gogogadget is my technical blog. This is where I document my ongoing hobby-projects in electronics, software and other things I find interesting.
                    The format of the blog will probably vary a lot from one post to another based on how much time I have on hand and how interesting I find a specific project.
                    In general, I plan to split the blog into three parts: Electronics, Software, and Ideas (there will probably be a lot of overlap).
                </h2>
            </div>

        </div>

    </section>

</main>

<style>

    section{
        padding-bottom: 30px;
    }

    .title{
        padding: 20px 0px;
    }

    figure.blogpost{
        margin-bottom: 1rem;
        -webkit-transition: all .1s ease-in-out;
        transition: all .1s ease-in-out;
        border-radius: 5px;
        background-size: cover;
        background-repeat: no-repeat;
        box-shadow: 0 5px 20px rgba(14, 25, 80, 0.3);
    }

    figure.blogpost:hover{
        -webkit-transform: scale(1.055) translateY(-2px);
        transform: scale(1.055) translateY(-2px);
        -webkit-box-shadow: 0 2px 25px 0 rgba(30, 30, 30, 0.1);
        box-shadow: 0 2px 25px 0 rgba(30, 30, 30, 0.1);
    }

</style>
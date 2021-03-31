<script lang="ts">

	import Blog from '../routes/Blog.svelte'

	import 'bulma/css/bulma.css'

	import Header from '../src/Header.svelte'
	import About from '../src/About.svelte'
	import Skills from '../src/Skills.svelte'
	import Experience from '../src/Experience.svelte'
	import Contact from '../src/Contact.svelte'
	import Footer from '../src/Footer.svelte'

</script>

<svelte:head>
	<title>Chris Vaksdal</title>
	<html lang="en" />
</svelte:head>

<main>

	<Header 

		professions = {[
			"Electronics Engineer",
			"Embedded Systems Engineer",
			"Web Developer",
			"System Developer",
		]}

		navItems = {[
/* 			{ label: "About me", href: "", id: "#about-section"},
 *//* 			{ label: "Skills", href: "", id: "#skills-section"},
 *//* 			{ label: "Experience", href: "", id: "#experience-section"},
 */			{ label: "Contact", href: "", id: "#contact-section"},
			{ label: "Blog", href: "/blog", id: ""},
		]}

	  />
	
	<section class="main-content">
		
		<section id="about-section">
<!-- 			<About />
 -->		</section>
		
		<section id="skills-section">
<!-- 			<Skills />
 -->		</section>
		
		<section id="experience-section">
<!-- 			<Experience />
 -->		</section>
		
		<section id="contact-section">
			<Contact />
		</section>

	</section>

</main>

<style>

	.main-content{
		padding: 60px 0px;
	}

</style>
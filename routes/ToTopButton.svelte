<script>

    import Icon from 'fa-svelte'
	import { faAngleUp } from '@fortawesome/free-solid-svg-icons/faAngleUp'
	import { scrollToTop } from "svelte-scrollto"

    const icon = faAngleUp
	
	window.onscroll = () => {
		if (document.body.scrollTop > 30 || document.documentElement.scrollTop > 30) {
			document.getElementById("toTopButton").style.display = "block"
		} else {
			document.getElementById("toTopButton").style.display = "none"
		}
	};

</script>

<form on:click={() => scrollToTop()} action="#home">
    <div id="toTopButton">
        <Icon icon={icon} />
    </div>
</form>

<style>

    #toTopButton{
		text-align: center;
		height: 50px;
		width: 50px;
		display: none;
		position: fixed;
		bottom: 20px;
		right: 30px;
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
    
</style>
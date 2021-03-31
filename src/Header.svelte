<script lang="ts">

  import Navbar from "./Navbar.svelte";

  export let navItems: Array<{label: string, href: string, id: string}>
  
  export let professions: Array<string>
  
  const professionSwitchingInterval = 1000; // How often displayed profession is switched.

  let professionIndex: number = 0;
  let numProfessions: number = professions.length;

  setInterval(() => {
    professionIndex++;
    professionIndex %= numProfessions;
  }, professionSwitchingInterval);

</script>

<header>
  
    <div class="header-wrapper" id="home">
      <section class="hero is-large">

        <div class="hero-body">
          <div class="container has-text-centered">
            <h1 class="subtitle">Hi! I'm</h1>
            <h2 class="title">Christoffer-Robin Vaksdal</h2>
            <h1 class="subtitle">
              <span class="profession">
                {#key professions[professionIndex]}
                  <span>{professions[professionIndex]}</span>
                {/key}
              </span>
            </h1>
          </div>
        </div>

        <Navbar navItems = {navItems}/>
        
      </section>
    </div>

</header>

<style>

  /* Header content */

  .hero{
      background: linear-gradient(rgba(31, 44, 108, 0.65), rgba(31, 44, 108, 0.65)), rgba(0, 0, 0, 0.55) url("/images/background.jpg") no-repeat;
      background-size: cover;
      background-attachment: fixed;
  }

  .hero .title {
    font-family: 'Kaushan Script', sans-serif;
    font-size: 5rem;
    color: whitesmoke;
  }

  .hero .subtitle {
    padding: 5px;
    color: whitesmoke;
  }

  .hero .profession {
    padding-top: 50px;
    font-size: 1.7rem;
    text-transform: uppercase;
  }
  
</style>
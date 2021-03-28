<script>
import Navbar from "./Navbar.svelte";

</script>
<header>
    <div class="header-wrapper" id="home">
      <section class="hero is-large">
        <div class="hero-body">
          <div class="container has-text-centered">
            <h1 class="subtitle">Welcome.</h1>
            <h2 class="title">Christoffer-Robin Vaksdal</h2>
            <h1 class="subtitle profession">Electronics Engineer</h1>
          </div>
        </div>
        <Navbar></Navbar>
        </section>
    </div>
</header>

<style>
    .hero{
        background: linear-gradient(rgba(31, 44, 108, 0.65), rgba(31, 44, 108, 0.65)), rgba(0, 0, 0, 0.55) url("/static/background.jpg") no-repeat;
    }
</style>
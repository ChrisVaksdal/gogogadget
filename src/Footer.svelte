<script lang="ts">

  import 'bulma/css/bulma.css'

  function getCurrentYear(){
    const today = new Date()
    const currentYear: string = today.getFullYear().toString()
    return currentYear
  }

</script>

<footer class="footer">
  <p>
    <strong class="white">Gogogadget</strong> by <a href="https://christoffer-robin.no">Chris Vaksdal</a>.
    The source code is not licensed yet under <a href="http://opensource.org/licenses/mit-license.php">MIT</a>.<br>
    The website content is licensed is not yet licensed under <a href="http://creativecommons.org/licenses/by-nc-sa/4.0/">CC BY NC SA 4.0</a>.<br>
    Image copyright Christoffer-Robin Vaksdal {getCurrentYear()}.
  </p>

</footer>

<style>
  
  .footer {
    bottom: 0;
    width: 100vw;
    padding: 0;
    line-height: 30px;
    text-align: center;
    background: whitesmoke;
    color: grey;
    padding-top: 1rem;
    margin-bottom: 1rem;
}

</style>
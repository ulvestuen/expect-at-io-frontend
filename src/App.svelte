<script>
  import Nav from "./Nav.svelte";
  import MainMatter from "./MainMatter.svelte";

  let currentMain = "";

  function handleNavigation(event) {
    currentMain = event.detail.text;
  }
</script>

<style>
  .top {
    width: 100%;
    height: 2em;
    margin: 2em;
  }
  h1 {
    color: grey;
    text-transform: uppercase;
    font-size: 3em;
    font-weight: 100;
  }
</style>

<div class="top">
  <h1>Expect At I/O</h1>
</div>
<Nav on:navigate={handleNavigation} />
<MainMatter content={currentMain} />

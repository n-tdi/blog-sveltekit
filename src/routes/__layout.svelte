<script>
  import Nav from "$lib/Nav.svelte";
</script>

<div class="container">
  <div class="top--container">
    <Nav />
  </div>
  <div class="container--bottom">
    <slot />
  </div>
</div>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap');

  .container {
    font-family: 'Roboto', sans-serif;
  }
  .container--bottom {
    max-width: 88%;
    margin: 0 auto;
  }
</style>

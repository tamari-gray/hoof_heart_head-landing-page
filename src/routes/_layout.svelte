<script>
  import Nav from "../components/Nav.svelte";
</script>

<style>
  main {
    position: relative;
    z-index: 10;
    margin: 0 auto;
    box-sizing: border-box;
  }
</style>

<Nav />

<main>
  <slot />
</main>

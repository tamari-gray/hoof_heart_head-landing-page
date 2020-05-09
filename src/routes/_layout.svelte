<script>
  import Nav from "../components/Nav.svelte";
</script>

<style>
  /* * {
    outline: 5px solid red;
  } */
  main {
    position: relative;
    z-index: 10;
    margin: 0 auto;
    box-sizing: border-box;
  }
  .background-img {
    height: 80vh;
    width: 100vw;
    position: absolute;
    z-index: 0;
    opacity: 0.5;
  }
  .gradient {
    height: 100vh;
    width: 100vw;
    position: absolute;
    z-index: 10;
    /* background: #8e2de2; fallback for old browsers */
    /* background: -webkit-linear-gradient(
      to right,
      #4a00e0,
      #8e2de2
    ); Chrome 10-25, Safari 5.1-6 */
    /* background: linear-gradient(
      to right,
      #4a00e0,
      #8e2de2 */
    /* ); W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
  }
</style>

<!-- <img src="grandad_love.jpg" class="img-fit-cover background-img " alt="..." />
<div class="gradient" /> -->

<Nav />

<main>
  <slot />
</main>

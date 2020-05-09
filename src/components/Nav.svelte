<script>
  export let segment;
</script>

<style>
  @font-face {
    src: url(chela.ttf);
    font-family: chela;
  }
  nav {
    /* border-bottom: 1px solid #b0ff57; */
    font-weight: 300;
    padding: 0 1em;
    font-family: "Raleway", sans-serif;
  }

  ul {
    margin: 0;
    padding: 0;
  }

  /* clearfix */
  ul::after {
    content: "";
    display: block;
    clear: both;
  }

  li {
    display: block;
    /* float: left; */
    margin: auto;
    font-size: 1.25em;
  }

  [aria-current] {
    position: relative;
    display: inline-block;
  }

  [aria-current]::after {
    position: absolute;
    content: "";
    width: calc(100% - 1em);
    height: 2px;
    /* background-color: #76ff03; */
    display: block;
    bottom: -1px;
  }

  a {
    text-decoration: none !important;
    padding: 1em 0.5em !important ;
    display: block !important;
    color: black !important;
  }
</style>

<nav>
  <ul>
    <li>
      <a aria-current={segment === undefined ? 'page' : undefined} href=".">
        Hoof Heart Head
      </a>
    </li>

    <!-- <li><a aria-current='{segment === "about" ? "page" : undefined}' href='about'>about</a></li> -->

    <!-- for the blog link, we're using rel=prefetch so that Sapper prefetches
		     the blog data when we hover over the link or tap it on a touchscreen -->
    <!-- <li><a rel=prefetch aria-current='{segment === "blog" ? "page" : undefined}' href='blog'>blog</a></li> -->
  </ul>
</nav>

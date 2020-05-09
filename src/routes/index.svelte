<script>
  import * as animateScroll from "svelte-scrollto";
  var audio = new Audio("fart_sound_scroll.mp3");

  function playFart() {
    audio.muted = false;
    audio.play();
  }

  // function scroll() {
  //   y = 110;
  // }

  let y;

  $: if (y >= 100) {
    console.log(`playing fart!`);
    playFart();
  } else {
    audio.muted = true;
  }
</script>

<style>
  @font-face {
    src: url(chela.ttf);
    font-family: chela;
  }
  h1,
  p {
    margin: 0 auto;
    color: black;
    font-family: "Raleway", sans-serif;
  }

  h1 {
    font-size: 2em;
    margin: auto;
  }
  p {
    margin-bottom: 0.3em;

    font-size: 0.8em;
    font-family: roboto;

    margin-top: 1em;
  }

  .space-top {
    height: 10vh;
  }
  .bottom-space {
    height: 11vh;
  }

  .subText {
    font-size: 1em;
    margin-top: 0.8em;
    font-style: italic;
    font-family: "Roboto";
  }

  img {
    height: 150px;
    -ms-transform: rotate(15deg);
    transform: rotate(15deg);
  }

  @media (min-width: 380px) {
    .warm-break {
      display: none;
    }
    img {
      height: 170px;
    }
    .bottom-space {
      height: 16vh;
    }
  }

  @media (min-width: 480px) {
    h1 {
      font-size: 2em;
    }
    .space-top {
      height: 20vh;
    }
    .subText,
    p {
      font-size: 1em;
    }
    .cont {
      padding-left: 0.4rem;
    }
    img {
      height: 250px;
    }
  }

  @media (min-width: 1000px) {
    h1 {
      font-size: 3em;
    }
    img {
      height: 300px;
    }
  }
</style>

<svelte:head>
  <title>Sapper project template</title>
</svelte:head>

<svelte:window bind:scrollY={y} />

<div class="container cont">
  <div class="columns">
    <div class="column col-8 col-mx-auto">

      <div class="space-top" />
    </div>
    <div class="column col-12 columns">
      <div class="columns column col-sm-12 col-8 col-ml-auto">
        <div class="column col-12 col-sm-10 col-mx-auto">
          <h1>
            Feel your families
            <!-- <span style="color: #76ff03; font-style: italic">warm</span> -->
            <span style="color: #76ff03">warm</span>
            <br class="warm-break" />
            energy, by sending them
            <br />
            <span style="color: #76ff03;">YOUR FARTS!</span>
          </h1>
          <h1 class="subText" style="">
            Coming soon for
            <br />
            Iphone & Android
          </h1>

        </div>

        <div class="column col-12" style="height: 2.5vh" />

        <div class="column col-8 col-sm-10 col-mx-auto">
          <p>Sign up to get early access now!</p>
          <div class="input-group">
            <input
              type="text"
              class="form-input"
              placeholder="Email address"
              on:click={() => animateScroll.scrollToBottom()} />
            <button
              class="btn btn-primary input-group-btn"
              style="background: #EB03FF; border-color:#A400B3 ">
              Sign up
            </button>
          </div>
        </div>
      </div>
      <div class="column col-12 bottom-space" style="" />
      <div class="column col-sm-4 col-mx-auto col-3">
        <img src="app_mockup.png" style="" alt="..." />
      </div>
    </div>
  </div>
</div>

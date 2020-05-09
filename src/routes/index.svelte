<script>
  import * as animateScroll from "svelte-scrollto";

  import { onMount } from "svelte";
  let db, audio;

  onMount(() => {
    db = firebase.firestore();
    audio = new Audio("fart_sound_scroll.mp3");
    audio.muted = true;
  });

  function playFart() {
    audio.muted = false;
    audio.play();
  }

  let y;

  let showOverlay = false;

  // form validation
  let email = "";
  let emailIsValid = false;
  let showError = false;

  function validateEmail() {
    console.log("validating:", email);
    email && /(^\w.*@\w+\.\w)/.test(email) ? submitEmail() : validationError();
  }

  function validationError() {
    console.log("invalid email");
    showError = true;
  }

  async function submitEmail() {
    animateScroll.scrollToTop();
    //put in firebase
    await db
      .collection("family")
      .add({ email: email })
      .then(function(docRef) {
        emailIsValid = true;
        showError = false;
        console.log(email, "is valid");
        showOverlay = true;
      })
      .catch(function(error) {
        console.error("Error adding email to firebase: ", error);
      });
  }

  function reset() {
    showOverlay = false;
    emailIsValid = false;
    email = "";
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

  .email-error-message {
    display: none;
  }

  .input-error {
    border: thin solid rgba(255, 0, 0, 0.3);
  }

  .show {
    display: block !important;
    color: rgba(255, 0, 0, 0.5);
  }

  .space-top {
    height: 10vh;
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
    margin-top: 15vh;
  }

  .img-parent {
    margin: auto;
  }

  .left-side-padding {
    margin-left: 5vw;
  }

  .cont {
    position: relative;
    z-index: 0;
  }

  @media (min-width: 385px) {
    .warm-break {
      display: none;
    }
    img {
      height: 150px;
      margin-top: 22vh;
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

  @media (min-width: 600px) {
    img {
      margin-top: 0;
    }
    .left-side-padding {
      margin-left: 5vw;
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

  @media (min-width: 1350px) {
    .warm-break {
      display: block;
    }
    .left-side-padding {
      margin-left: 10vw;
    }
  }

  .overlay {
    position: fixed;
    z-index: 100;
    width: 100vw;
    height: 100vh;
    background-color: rgba(0, 0, 0, 0.74);
    display: none;
  }

  .showOverlay {
    display: block;
  }

  .popup {
    width: 80vw;
    height: 50vh;
    margin-top: 20vh;
  }
</style>

<svelte:head>
  <title>Hoof Heart Head</title>
</svelte:head>

<svelte:window bind:scrollY={y} />

<div class="overlay" class:showOverlay>
  <div class="popup container">
    <div
      class="card"
      style="border-radius: 7.5px; max-width: 340px; margin: auto">

      <div class="card-header">
        <div class="card-title h5">Thanks for signing up &#128516 &#128516</div>
      </div>
      <div class="card-body">
        Well let you know when were close to launching so
        <span style="font-weight: bold; color: #A400B3">
          you can be one of the first
        </span>
        to try out
        <span style="font-weight: bold">Hoof Heart Head!</span>

      </div>
      <div class="card-footer">
        <button
          on:click={reset}
          class="btn "
          style="color: #A400B3; border: .05rem solid #A400B3;">
          close
        </button>
      </div>
    </div>
  </div>
</div>

<div class="container cont">
  <div class="columns">
    <div class="column col-8 col-mx-auto">

      <div class="space-top" />
    </div>
    <div class="column col-xl-12 col-11 col-mx-auto columns">
      <div
        class="columns column col-sm-12 col-xl-8 col-6 col-ml-auto
        left-side-padding">
        <div class="column col-12 col-sm-10">
          <h1>
            Feel your families
            <span style="color: #76ff03">warm</span>
            <br class="warm-break" />
            energy, by sending them
            <br />
            <span style="color: #76ff03;">YOUR FARTS!</span>
          </h1>
          <h1 class="subText" style="">Coming soon to IOS & Android...</h1>

        </div>

        <div class="column col-12" style="height: 2.5vh" />

        <div class="column col-12 col-sm-10 col-mr-auto">
          <p>
            Sign up to get
            <span style="font-weight: bold;">early access</span>
            now!
          </p>
          <div class="input-group">
            <input
              size="23"
              type="email"
              class:input-error={showError}
              class:input-success={emailIsValid}
              placeholder="Email address"
              bind:value={email}
              on:click={() => {
                animateScroll.scrollToBottom();
                playFart();
                showError = false;
              }} />
            <button
              class="btn btn-primary input-group-btn"
              style="background: #EB03FF; border-color:#A400B3 "
              on:click={validateEmail}>
              Sign up
            </button>
          </div>
          <p class="email-error-message" class:show={showError}>
            please enter a valid email
          </p>
        </div>
      </div>
      <div class="column col-3 img-parent ">
        <img src="app_mockup.png" style="" alt="..." />
      </div>
    </div>
  </div>
</div>

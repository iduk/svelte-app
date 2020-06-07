<script>
  export let date;
  // onMount
  import { onMount } from "svelte";
  onMount(async () => {
    const res = await fetch("/api/date");
    const newDate = await res.text();
    date = newDate;
  });
  // Modal
  import Modal from "./Components/Modal.svelte";
  let showModal = false;
</script>

<svelte:head>
  <p>{date ? date : 'Loading date...'}</p>

  <style lang="scss">
    @import "./Scss/Styles.scss";
  </style>
</svelte:head>

<main>
  <h1>Svelte + Node.js API ㅋㅋ</h1>
  <h2>
    Deployed with
    <a href="https://vercel.com/docs" target="_blank" rel="noreferrer noopener">
      Vercel
    </a>
    !
  </h2>

  <p>
    <a
      href="https://github.com/vercel/vercel/tree/master/examples/svelte"
      target="_blank"
      rel="noreferrer noopener">
      This project Test
    </a>
    is a
    <a href="https://svelte.dev/">Svelte</a>
    app with three directories,
    <code>/public</code>
    for static assets,
    <code>/src</code>
    for components and content, and
    <code>/api</code>
    which contains a serverless
    <a href="https://nodejs.org/en/">Node.js</a>
    function. See
    <a href="/api/date">
      <code>api/date</code>
      for the Date API with Node.js
    </a>
    .
  </p>
  <br />
  <h2>The date according to Node.js is:</h2>

  <button on:click={() => (showModal = true)}>show modal</button>

  {#if showModal}
    <Modal on:close={() => (showModal = false)}>
      <h2 slot="header">
        modal
        <small>
          <em>adjective</em>
          asdfasdfasdfa
        </small>
      </h2>
    </Modal>
  {/if}

</main>

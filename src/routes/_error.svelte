<script>
  export let status;
  export let error;

  const dev = process.env.NODE_ENV === "development";
</script>

<style type="text/scss">
  @import "@inc/uchu/src/scss/components/variables";
  @import "@inc/uchu/src/scss/components/mixins";

  section {
    padding: 1.75rem 1.5rem;
    max-width: 800px;
  }

  p {
    font-size: 1rem;
    line-height: 1.55;

    &:not(:last-child) {
      margin-bottom: 1rem;
    }
  }
</style>

<svelte:head>
  <title>{status}</title>
</svelte:head>

<section>
  <h1>Whoops &middot; {status}</h1>

  {#if status === 404}
    <p>Go back <a href="." title="Back to the homepage">home</a></p>
  {:else}
    <p>{error.message}</p>
  {/if}

  {#if dev && error.stack}
    <pre>{error.stack}</pre>
  {/if}
</section>

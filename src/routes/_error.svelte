<script>
  // constants
  import errors from '../_errors'

  // utils
  import { getPageTitle } from '../_utils'

  // props
  export let status
  export let error

  const dev = process.env.NODE_ENV === 'development'
  const page = {
    title: `Error ${status}`,
  }
</script>

<svelte:head>
  <title>{getPageTitle(page)}</title>
</svelte:head>

<h1>{page.title}</h1>

{#if errors[status]}
  <h2>{errors[status].short}</h2>

  {#if errors[status].long}
    <p>{errors[status].long}</p>
  {/if}
{:else}
  <h2>{error.message}</h2>
{/if}

{#if dev && error.stack}
  <pre class="debug error">{error.stack}</pre>
{/if}

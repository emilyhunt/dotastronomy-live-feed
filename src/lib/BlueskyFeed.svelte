<script>
  import { onMount } from "svelte";
  export let search = "#test";
  export let refreshDelay = 60;

  let time = new Date();
  $: lastRefreshTime = time.getTime();

  onMount(() => {
    const interval = setInterval(() => {
      time = new Date();
    }, 1000 * refreshDelay);

    return () => {
      clearInterval(interval);
    };
  });
</script>

<h2>Bluesky {search} feed:</h2>
{#key lastRefreshTime}
  <bsky-embed
    {search}
    mode="dark"
    limit="20"
    link-target="_blank"
    link-image="false"
    custom-styles={".border-slate-300 {border-color: #ffffff;} article {margin-bottom: 10px; border: 1px solid; border-radius: 10px; background-color: #004765}"}
  />
{/key}

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

<h2>Bluesky {search} live feed:</h2>
{#key lastRefreshTime}
  <bsky-embed
    {search}
    mode="dark"
    limit="20"
    link-target="_blank"
    link-image="false"
    custom-styles={".border-slate-300 {border: 0px;} .border-slate-800 {border: 1px solid;}"}
  />
{/key}

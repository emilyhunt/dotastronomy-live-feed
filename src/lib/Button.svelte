<script>
  export let click;
</script>

<button on:click={click}>
  <slot />
</button>

<style>
  button {
    border: 0px solid;
    border-color: white;
    border-radius: 5px;
    background-color: #004765;
    color: white;
  }
  button:hover {
    background-color: #006b99;
  }

</style>

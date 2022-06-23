<script>
  import Bubble from "./Bubble.svelte";

  export let messages = [];
</script>

<div>
  {#each messages as message}
    <Bubble {message} />
  {/each}
</div>

<style>
  div {
    display: flex;
    flex-direction: column;
    padding: 12px;
  }
</style>

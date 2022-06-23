<script>
  import Date from "./Date.svelte";

  export let message = {};
</script>

<div>
  {message.text}

  <Date {message} />
</div>

<style>
  div {
    padding: 6px 10px;
  }
</style>

<script>
  import Date from "./Date.svelte";
  export let message = {};
</script>

<div class={message.from}>
  <img src={message.file} alt="Image" />

  <Date {message} />
</div>

<style>
  div {
    overflow: hidden;
    border-radius: 8px;
    border-top-right-radius: 14px;
    border-bottom-right-radius: 14px;
  }

  div.user {
    border-radius: 14px;
  }

  img {
    max-width: 100%;
  }
</style>

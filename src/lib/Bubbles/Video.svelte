<script>
  import Date from "./Date.svelte";
  export let message = {};
</script>

<div class={message.from}>
  <video src={message.file} controls>
    Sorry, your browser doesn't support embedded videos, but don't worry, you
    can <a href="videofile.ogg">download it</a>
    and watch it with your favorite video player!
  </video>

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

  video {
    max-width: 100%;
  }
</style>

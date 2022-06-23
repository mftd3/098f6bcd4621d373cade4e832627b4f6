<script>
  import Audio from "./Audio.svelte";
  import Text from "./Text.svelte";
  import Image from "./Image.svelte";
  import Video from "./Video.svelte";

  export let message = {};

  const types = {
    audio: Audio,
    text: Text,
    image: Image,
    video: Video,
  };

  $: component = types[message.type];
</script>

<div class="bubble {message.from}">
  {#if component}
    <svelte:component this={component} {message} />
  {/if}
</div>

<style>
  .bubble {
    background: #fff;
    max-width: 86%;
    border-radius: 9px;
    margin-bottom: 7px;
    line-height: 1.18em;
    position: relative;
    filter: drop-shadow(0px 0px 0.5px #c6c6c6);
    padding: 1px;
  }

  .bubble.user {
    align-self: end;
    border-radius: 15px;
    background-color: #e1fec6;
  }

  .bubble::before {
    content: "";
    display: block;
    width: 10px;
    height: 6px;
    background-image: url("../../assets/message_arrow-right.svg");
    position: absolute;
    top: 100%;
    left: 0;
    background-size: cover;
    transform: translate(-36%, -100%);
    z-index: -1;
  }

  .bubble.user:before {
    left: auto;
    right: 0;
    background-image: url("../../assets/message_arrow-left.svg");
    transform: scale(-1, 1) translate(-16%, -100%);
  }

  .bubble.bot {
    align-self: start;
    border-top-right-radius: 15px;
    border-bottom-right-radius: 15px;
  }
</style>

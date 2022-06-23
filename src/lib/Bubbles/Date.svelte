<script>
  export let message = {};

  let date = new Date(message.date * 1000),
    hours = date.getHours(),
    minutes = date.getMinutes();
</script>

<span class="{message.from} type-{message.type}">
  {hours}:{minutes}
  <div class="date">
    {hours}:{minutes}
  </div>
</span>

<style>
  span {
    visibility: hidden;
    display: inline-flex;
  }

  div {
    position: absolute;
    right: 10px;
    bottom: 2px;
    display: inline-block;
    color: #979797;
    font-size: 10px;
    vertical-align: bottom;
    visibility: visible;
  }

  span.type-audio,
  span.type-video,
  span.type-image {
    position: absolute;
    right: 0px;
    bottom: 5px;
  }

  .user div {
    color: #2da32f;
  }

  .type-video div,
  .type-image div {
    padding: 0 10px;
    background-color: rgba(0, 0, 0, 0.6);
    border-radius: 25px;
    color: #fff;
  }
</style>

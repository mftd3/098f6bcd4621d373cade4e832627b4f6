<script>
  import Avatar from "./Avatar.svelte";

  let time = new Date();
  $: hours = time.getHours();
  $: minutes = time.getMinutes();

  let letter = "t";
</script>

<div class="header">
  <div class="header-system">
    <div class="clock">{hours}:{minutes}</div>
  </div>
  <div class="header-app">
    <div class="header-back">Back</div>
    <div class="header-title">
      testgeratest_bot
      <div class="header-subtitle">bot</div>
    </div>
  </div>
  <Avatar {letter} />
</div>

<style>
  .header {
    display: flex;
    flex-wrap: wrap;
    height: 87px;
    background-color: #eef0ed;
    position: relative;
    z-index: 1;
    padding: 3px 8px;
  }

  .header-system {
    height: 50px;
    width: 100%;
  }

  .header-back {
    background-image: url("/assets/back.png");
  }
</style>

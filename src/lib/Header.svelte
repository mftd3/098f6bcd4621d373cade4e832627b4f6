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
    <div class="battery">
      <div class="battery-level" />
    </div>
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
    height: 40px;
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
  }

  .header-back {
    background-image: url("/assets/back.png");
  }

  .battery {
    height: 11px;
    width: 22px;
    border-radius: 3px;
    border: 1px solid #838383;
    position: relative;
    padding: 1px;
  }

  .battery:before {
    content: "";
    display: flex;
    height: 4px;
    width: 1.5px;
    background: #747474;
    position: absolute;
    right: -3px;
    top: calc((9px - 4px) / 2);
    border-top-right-radius: 10px;
    border-bottom-right-radius: 10px;
  }

  .battery-level {
    height: 7px;
    width: 18px;
    background-color: #5bc236;
    border-radius: 1px;
  }

  .clock {
    font-weight: 600;
    font-size: 1.1em;
  }

  .header-app {
    display: flex;
  }
</style>

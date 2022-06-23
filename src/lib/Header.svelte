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
    <div class="header-avatar">
      <Avatar {letter} />
    </div>
  </div>
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
    border-bottom: 1px solid #c8c7cb;
  }

  .header-system {
    height: 40px;
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
  }

  .battery {
    height: 11px;
    width: 22px;
    border-radius: 3px;
    border: 1px solid #8e908c;
    position: relative;
    padding: 1px;
  }

  .battery:before {
    content: "";
    display: flex;
    height: 4px;
    width: 1.5px;
    background: #767774;
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
    flex-basis: 16%;
    text-align: center;
  }

  .header-app {
    display: flex;
    width: 100%;
    justify-content: space-between;
    align-items: center;
  }

  .header-title {
    text-align: center;
    font-weight: 600;
    font-size: 1.2em;
    flex-basis: 50%;
  }

  .header-subtitle {
    font-weight: 400;
    font-size: 0.8em;
    color: #787878;
  }

  .header-back {
    color: #3478f6;
    font-size: 1.25em;
    line-height: 24px;
    height: 24px;
    padding-left: 20px;
    background-image: url("../assets/back.png");
    background-repeat: no-repeat;
    background-size: contain;
    flex-basis: 25%;
  }

  .header-avatar {
    flex-basis: 25%;
    display: flex;
    justify-content: right;
  }
</style>

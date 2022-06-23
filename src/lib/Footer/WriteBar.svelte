<script>
  export let large = false;
  export let message = "";

  $: canSend = message.length > 0;
</script>

<div class="wrapper" class:large>
  <div class="inner">
    <div class="action">
      <button class="menu">menu</button>
    </div>
    <div class="action">12</div>
    <div class="action large">
      <input type="text" placeholder="Message" bind:value={message} />
    </div>
    <div class="action">3</div>
    {#if canSend}
      <div class="action">
        <button class="menu">send</button>
      </div>
    {/if}
  </div>
</div>

<style>
  .wrapper {
    border-top: 0.5px solid #b2b2b2;
    background-color: rgba(255, 255, 255, 0.8);
  }
  .wrapper.large {
    height: 79px;
  }
  .inner {
    height: 45px;
    padding: 0 6px;
    gap: 6px;
    display: flex;
    align-items: center;
  }
  .action {
    display: flex;
    align-items: center;
    justify-content: center;
    min-width: 30px;
  }
  .action.large {
    flex-grow: 1;
  }
  .menu {
    display: flex;
    align-items: center;
    height: 33px;
    border-radius: 30px;
    background: #007aff;
    color: #fff;
    padding: 0 12px;
  }

  input {
    width: 100%;
    height: 33px;
    border: 1px solid #e5e5e5;
    border-radius: 20px;
    padding-left: 14px;
  }
  input::placeholder {
    color: #bebec0;
  }
</style>

<script>
  export let active = false;
  export let onClick = null;
</script>

<button class:active on:click={onClick}>
  <span class="symbol" />
  <span class="label"><slot /></span>
</button>

<style>
  .active {
    color: #007aff;
  }
  .active .symbol {
    background-color: #007aff;
  }
  button {
    background-color: transparent;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    width: 48px;
    height: 49px;
  }
  .symbol {
    width: 26px;
    height: 26px;
    background-color: #959595;
    border-radius: 100%;
  }
  .label {
    font-size: 10px;
    line-height: 12px;
    font-weight: 500;
    margin-top: 6px;
  }
</style>

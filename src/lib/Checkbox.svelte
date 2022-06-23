<script>
  export let number = 0;
  export let checked = false;
  export let onSelected = null;
</script>

<div class:checked on:click={onSelected}>
  {#if checked}
    {number}
  {/if}
</div>

<style>
  div {
    display: flex;
    align-items: center;
    justify-content: center;

    width: 26px;
    height: 26px;
    border: 2px solid #fff;
    border-radius: 100%;
    box-shadow: 0 0 5px #000;

    color: #fff;
  }
  div.checked {
    background-color: #007aff;
  }
</style>

<script>
  export let onCancelClick = null;
</script>

<div class="inner">
  <div class="aside left" on:click={onCancelClick}>Cancel</div>
  <div class="title"><slot /></div>
  <div class="aside right">icon</div>
</div>

<style>
  .inner {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 16px;
    width: 100%;
    height: 56px;
  }
  .aside {
    color: #007aff;
    font-size: 17px;
    line-height: 20px;
    font-weight: 300;
  }
  .title {
    font-size: 17px;
    line-height: 22px;
    font-weight: 600;
  }
</style>

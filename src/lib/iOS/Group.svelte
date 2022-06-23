<script>
  export let header = "";
  export let footer = "";
  export let spaced = false;
</script>

<section>
  {#if header}
    <p>{header}</p>
  {/if}
  <div class:spaced><slot /></div>
  {#if footer}
    <p>{footer}</p>
  {/if}
</section>

<style>
  div {
    background-color: #fff;
  }
  .spaced {
    margin-right: 16px;
    margin-left: 16px;
  }
</style>

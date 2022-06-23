<script>
  export let letter = "";
</script>

<div class="avatar">
  {#if letter}
    <span>{letter}</span>
  {/if}
</div>

<style>
  .avatar {
    background: linear-gradient(to top, #4acccd, #00fcfd);
    display: flex;
    align-items: center;
    justify-content: center;
    width: 36px;
    height: 36px;
    border-radius: 100%;
  }

  .avatar span {
    color: #fff;
    font-size: 1.1em;
    font-weight: 900;
    text-transform: uppercase;
  }
</style>

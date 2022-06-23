<script>
  export let large = false;
</script>

<div class="wrapper" class:large>
  <div class="inner">
    <div class="action">
      <div class="menu">menu</div>
    </div>
    <div class="action">1</div>
    <input type="text" placeholder="Message" />
    <div class="action">2</div>
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
    padding: 0 10px;
    display: flex;
    align-items: center;
  }
  .action {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 45px;
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
    flex-grow: 1;
    height: 33px;
    border: 1px solid #e5e5e5;
    border-radius: 20px;
  }
</style>

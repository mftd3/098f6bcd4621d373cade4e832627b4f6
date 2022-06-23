<div>
  <slot />
</div>

<style>
  div {
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 10000;

    background-color: #fff;
    border-radius: 10px;
    border-bottom-left-radius: 0;
    border-bottom-right-radius: 0;

    background: rgba(249, 249, 249, 0.94);
    box-shadow: 0px -0.5px 0px rgba(0, 0, 0, 0.3);
    backdrop-filter: blur(20px);
  }
</style>

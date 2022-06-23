<script>
  import Frame from "./lib/Frame.svelte";
  import Header from "./lib/Header.svelte";
  import { WriteBar, FooterButton, FooterButtonGroup } from "./lib/Footer";
</script>

<Frame>
  <div class="telegram">
    <div class="inner">
      <Header />
      <div class="body">2</div>
      <footer>
        <WriteBar />
        <FooterButtonGroup>
          <FooterButton>Запустити форму</FooterButton>
          <FooterButton>🏠 Головне меню</FooterButton>
        </FooterButtonGroup>
      </footer>
    </div>
  </div>
</Frame>

<style>
  .telegram {
    position: relative;
    width: 375px;
    height: 812px;
  }
  .telegram::before,
  .telegram::after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
  }
  .telegram::before {
    background-image: url("assets/bg-color.png");
    background-repeat: repeat;
  }
  .telegram::after {
    background-image: url("assets/bg-pattern.png");
  }
  .inner {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 1;
  }
  footer {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
  }
</style>

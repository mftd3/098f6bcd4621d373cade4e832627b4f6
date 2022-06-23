<script>
  import { Bubbles } from "./lib/Bubbles";
  import {
    WriteBar,
    FooterButton,
    FooterButtonGroup,
    FooterButtonRow,
  } from "./lib/Footer";
  import Frame from "./lib/Frame.svelte";
  import Header from "./lib/Header.svelte";
</script>

<Frame>
  <div class="telegram">
    <div class="inner">
      <Header />
      <Bubbles />
      <footer>
        <WriteBar />
        <FooterButtonGroup>
          <FooterButtonRow>
            <FooterButton>слишком длинный текст</FooterButton>
            <FooterButton>13</FooterButton>
            <FooterButton>13</FooterButton>
            <FooterButton>14</FooterButton>
          </FooterButtonRow>
          <FooterButton>1</FooterButton>
          <FooterButton />
          <FooterButton>3</FooterButton>
          <FooterButton>4</FooterButton>
          <FooterButton>5</FooterButton>
          <FooterButton>6</FooterButton>
          <FooterButton>7</FooterButton>
          <FooterButton>8</FooterButton>
          <FooterButton>9</FooterButton>
          <FooterButton>10</FooterButton>
          <FooterButton>11</FooterButton>
          <FooterButton>12</FooterButton>
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

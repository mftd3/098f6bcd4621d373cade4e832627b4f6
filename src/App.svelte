<script>
  import API from "./mock";

  import { Bubbles } from "./lib/Bubbles";
  import {
    WriteBar,
    FooterButton,
    FooterButtonGroup,
    FooterButtonRow,
  } from "./lib/Footer";
  import Frame from "./lib/Frame.svelte";
  import Header from "./lib/Header.svelte";
  import AttachModal from "./modal/AttachModal.svelte";

  let modal = false;

  function toggle() {
    modal = !modal;
  }
</script>

<Frame>
  <div class="telegram">
    <div class="inner">
      <Header />
      <main>
        <Bubbles messages={API.messages} />
      </main>
      <footer>
        <WriteBar onAttachClick={toggle} />
        <FooterButtonGroup>
          {#each API.reply_markup.keyboard as row}
            <FooterButtonRow>
              {#each row as button}
                <FooterButton>{button.text}</FooterButton>
              {/each}
            </FooterButtonRow>
          {/each}
        </FooterButtonGroup>
      </footer>

      {#if modal}
        <AttachModal />
      {/if}
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
  main {
    overflow-y: auto;
    max-height: 1010px;
  }
  footer {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
  }
</style>

<script>
  import {
    PanelHeader,
    Modal,
    BottomBar,
    BottomBarItem,
    Contact,
    File,
    Gallery,
    Location,
    Poll,
  } from "../lib/iOS";

  let active = 0;

  const tabs = [
    { component: Gallery, symbol: "", label: "Gallery", title: "Gallery" },
    { component: File, symbol: "", label: "File", title: "File" },
    { component: Location, symbol: "", label: "Location", title: "Location" },
    { component: Poll, symbol: "", label: "Poll", title: "New Poll" },
    { component: Contact, symbol: "", label: "Contact", title: "Contacts" },
  ];

  $: component = tabs[active].component;
  $: tab = tabs[active];

  $: console.log(tab);
</script>

<Modal>
  <PanelHeader>{tab.title}</PanelHeader>
  <svelte:component this={component} />
  <BottomBar>
    {#each tabs as tab, index}
      <BottomBarItem onClick={() => (active = index)} active={index === active}>
        {tab.label}
      </BottomBarItem>
    {/each}
  </BottomBar>
</Modal>

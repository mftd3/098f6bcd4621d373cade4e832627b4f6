<script>
  import images from "../../../mock/gallery";
  import Checkbox from "../../Checkbox.svelte";

  let selected = [];

  function onSelected(index) {
    if (images[index].checked) {
      images[index].number = 0;
      images[index].checked = false;
      selected.splice(index, 1);
      console.log(selected);
    } else {
      images[index].number = selected.length + 1;
      images[index].checked = true;
      selected.push(index);
    }
  }
</script>

<div class="wrapper">
  <div class="item first" />

  {#each images as image, index}
    <div class="item" style:background-image="url({image.href})">
      <div class="checkbox">
        <Checkbox
          checked={image.checked}
          number={image.number}
          onSelected={() => onSelected(index)}
        />
      </div>
    </div>
  {/each}
</div>

<style>
  .wrapper {
    max-height: 417px;
    overflow-y: scroll;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
  }
  .item {
    position: relative;
    min-height: 124px;
    background-size: cover;
  }
  .item.first {
    background-color: green;
    grid-row-start: span 2;
  }
  .checkbox {
    position: absolute;
    top: 5px;
    right: 5px;
  }
</style>

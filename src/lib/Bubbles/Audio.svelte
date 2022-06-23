<script>
  import { onMount } from "svelte";
  //   import Date as DateBlock from "./Date.svelte";
  export let message = {};

  let url = message.file;
  let time = 0;
  let duration;
  let paused = true;
  let audio;
  let lastMouseDown;

  $: playback = format(duration - time);

  // Set up audio context
  window.AudioContext = window.AudioContext || window.webkitAudioContext;
  const audioContext = new AudioContext();

  function handleMousedown(e) {
    console.log(audio);
    lastMouseDown = new Date();
  }

  function handleMouseup(e) {
    if (new Date() - lastMouseDown < 300) {
      if (paused) audio.play();
      else audio.pause();
    }
  }

  console.log(audio);
  const drawAudio = (url) => {
    return fetch(url)
      .then((response) => response.arrayBuffer())
      .then((arrayBuffer) => audioContext.decodeAudioData(arrayBuffer))
      .then((audioBuffer) => filterData(audioBuffer));
  };

  const filterData = (audioBuffer) => {
    const rawData = audioBuffer.getChannelData(0); // We only need to work with one channel of data
    const samples = audioBuffer.duration < 5 ? 15 : 30; // Number of samples we want to have in our final data set
    const blockSize = Math.floor(rawData.length / samples); // the number of samples in each subdivision

    console.log(blockSize);

    const filteredData = [];
    for (let i = 0; i < samples; i++) {
      let blockStart = blockSize * i; // the location of the first sample in the block
      let sum = 0;
      for (let j = 0; j < blockSize; j++) {
        sum = sum + Math.abs(rawData[blockStart + j]); // find the sum of all the samples in the block
      }

      filteredData.push(sum / blockSize); // divide the sum by the block size to get the average
    }

    return normalizeData(filteredData);
  };

  const normalizeData = (data) => {
    let maxValue = Math.max(...data);

    let percentage = 20 / maxValue;

    return data.map((n) => n * percentage);
  };

  function format(seconds) {
    if (isNaN(seconds)) return "...";

    const minutes = Math.floor(seconds / 60);
    seconds = Math.floor(seconds % 60);
    if (seconds < 10) seconds = "0" + seconds;

    return `${minutes}:${seconds}`;
  }

  function getOpacity(time, index) {
    console.log(time);
    if (time < 1) {
      return "0.3";
    } else {
      return "1";
    }
  }

  let samples = [];

  onMount(async () => {
    samples = await drawAudio(url);
  });
</script>

<div class="audio {message.from}">
  <audio
    src={message.file}
    bind:currentTime={time}
    bind:duration
    bind:paused
    bind:this={audio}
  >
    Sorry, your browser doesn't support embedded audio
  </audio>

  <div class="audio-control">
    <div class="play" on:mousedown={handleMousedown} on:mouseup={handleMouseup}>
      {#if !paused}
        twix
      {:else}
        <img
          style="width: 30px;padding-left: 2px;"
          src="https://www.friidesigns.com/wp-content/uploads/2018/11/white-play-icon-png-6.png"
          alt="temp-arrow"
        />
      {/if}
    </div>
    <div class="waveform">
      <div class="sample-wrapper">
        {#each samples as sample, index}
          <div
            class="sample"
            style:height="{sample}px"
            style:opacity={getOpacity(time, index)}
          />
        {/each}
      </div>

      <div class="progress">
        {playback}
      </div>
    </div>
  </div>
</div>

<style>
  .play {
    width: 43px;
    height: 43px;
    border-radius: 100%;
    background-color: #2da32f;
    text-align: center;
    color: #fff;
    margin-right: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .audio-control {
    display: flex;
    padding: 10px 12px 11px 10px;
    align-items: center;
  }
  .sample-wrapper {
    width: 100%;
    display: flex;
    align-items: flex-end;
  }
  .sample {
    width: 2px;
    background-color: #2da32f;
    border-radius: 2px;
    margin-right: 2px;
    opacity: 0.3;
  }
  .progress {
    font-size: 9px;
    color: #2da32f;
  }
</style>

<svelte:options tag="floating-video" />

<script>
  import { onMount } from "svelte";

  export let posVertical = "bottom";
  export let posHorizontal = "right";
  export let src = null;

  let hidden = true;

  $: if (src) {
    hidden = false;
  }

  //Close floating video
  function closePip() {
    hidden = true;
    src = null;
  }

  //Drag floating video
  let moving = false,
    elmnt,
    nonePointer = false,
    pos1 = 0,
    pos2 = 0,
    pos3 = 0,
    pos4 = 0,
    posx = 0,
    posy = 0;

  function onMouseDown(e) {
    e = e || window.event;
    pos3 = e.clientX;
    pos4 = e.clientY;
    moving = true;
    nonePointer = true;
  }

  function onMouseMove(e) {
    if (moving) {
      e = e || window.event;
      pos1 = pos3 - e.clientX;
      pos2 = pos4 - e.clientY;
      pos3 = e.clientX;
      pos4 = e.clientY;
      posy = elmnt.offsetTop - pos2;
      posx = elmnt.offsetLeft - pos1;
      elmnt.style.top = `${posy}px`;
      elmnt.style.left = `${posx}px`;
    }
  }

  function onMouseUp() {
    if (moving) {
      moving = false;
      nonePointer = false;
    }
  }

  onMount(() => {
    elmnt.style[posHorizontal] = "0px";
    elmnt.style[posVertical] = "0px";
  });
</script>

<div bind:this={elmnt} id="pip" class:hidden data-resizable>
  <div class="topbar-floating-video">
    <div
      id="drag-pip"
      on:mousedown|preventDefault={onMouseDown}
      data-drag="pip"
    />
    <div id="close-pip" on:click={closePip} />
  </div>
  <div id="pip-content">
    {#if src}
      <iframe title="Floating Video Iframe" class:nonePointer {src} />
    {/if}
  </div>
</div>

<svelte:window
  on:mouseup={onMouseUp}
  on:mousemove|preventDefault={onMouseMove}
/>

<style>
  #pip {
    position: fixed;
    z-index: 20;
    background-color: black !important;
    height: max-content;
    width: max-content;
    min-width: min-content;
    padding: 0 0.5em 0.5em 0.5em;
    overflow: hidden;
    resize: both;
    display: flex;
    flex-direction: column;
  }
  #pip-content {
    flex: 1 1 auto;
  }
  #pip-content > * {
    height: 100%;
  }
  #pip-content iframe {
    width: 100%;
    height: 100%;
  }
  #pip > * {
    margin: 0 !important;
  }
  #close-pip {
    padding-left: 1rem;
    padding-right: 1rem;
    flex-shrink: 1;
  }
  #close-pip::after {
    display: inline-block;
    content: "×";
    font-size: large;
    cursor: pointer;
  }
  #drag-pip {
    cursor: move;
    padding-left: 1rem;
    padding-right: 1rem;
    width: 100%;
  }
  .topbar-floating-video {
    background-color: black;
    color: white;
    z-index: 25;
    display: flex;
  }
  .hidden {
    display: none !important;
  }
  div {
    pointer-events: auto;
  }
  iframe.nonePointer {
    user-select: none;
    pointer-events: none !important;
  }
  iframe {
    border-width: 0px;
    pointer-events: auto;
  }
</style>

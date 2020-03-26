<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  function setPage(event) {
    dispatch("navigate", {
      text: event.srcElement.innerHTML
    });
  }
</script>

<style>
  .navigation {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }
  .button {
    border-radius: 50%;
    border-width: 0.1em;
    border-style: solid;
    border-color: black;
    width: 6em;
    height: 6em;
    margin: 1em;
  }
  .arrow {
    border-width: 0em 0.2em 0.2em 0em;
    border-style: solid;
    border-color: black;
    height: 20px;
    width: 20px;
    margin: 3.2em 0em 0em 0em;
  }
  .right {
    transform: rotate(-45deg);
    -webkit-transform: rotate(-45deg);
  }
</style>

<nav class="navigation">
  <button class="button" on:click={setPage}>Load</button>
  <div class="arrow right" />
  <button class="button" on:click={setPage}>Input</button>
  <div class="arrow right" />
  <button class="button" on:click={setPage}>Output</button>
  <div class="arrow right" />
  <button class="button" on:click={setPage}>Run</button>
  <div class="arrow right" />
  <button class="button" on:click={setPage}>Results</button>
</nav>

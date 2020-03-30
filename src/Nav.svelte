<script>
    import {createEventDispatcher} from "svelte";

    const dispatch = createEventDispatcher();

    function setPage(event) {
        dispatch("navigate", {
            text: event.target.innerHTML
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

    .button:hover {
        border-width: 0.2em;
        font-weight: bold;
    }

    .arrow {
        border-width: 0 0.2em 0.2em 0;
        border-style: solid;
        border-color: black;
        height: 20px;
        width: 20px;
        margin: 3.2em 0 0 0;
    }

    .right {
        transform: rotate(-45deg);
        -webkit-transform: rotate(-45deg);
    }
</style>

<nav class="navigation">
    <button class="button" on:click={setPage}>Load</button>
    <div class="arrow right"></div>
    <button class="button" on:click={setPage}>TestCases</button>
    <div class="arrow right"></div>
    <button class="button" on:click={setPage}>Run</button>
    <div class="arrow right"></div>
    <button class="button" on:click={setPage}>Results</button>
</nav>

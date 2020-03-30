<script>
    async function runTest() {
        let response = await fetch("http://localhost:5000/run", {
            method: "POST"
        });
        let responseText = response.text();
        console.log(responseText);
    }
</script>

<style>
    .center {
        display: flex;
        justify-content: center;
    }

    .button {
        border-radius: 50%;
        border-width: 0.1em;
        border-style: solid;
        border-color: black;
        width: 10em;
        height: 10em;
        margin: 1em;
    }

    .button:hover {
        border-width: 0.2em;
        font-weight: bold;
    }
</style>

<section class="center">
    <button class="button" on:click={runTest}>START TEST</button>
</section>

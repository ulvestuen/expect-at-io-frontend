<script>
  function runTest(event) {
    fetch("http://localhost:5000/run", {
      method: "POST"
    })
      .then(response => response.text())
      .then(result => {
        console.log("Success:", result);
      })
      .catch(error => {
        console.error("Error:", error);
      });
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
</style>

<section class="center">
  <button class="button" on:click={runTest}>Load</button>
</section>

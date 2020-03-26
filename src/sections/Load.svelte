<script>
  let postmanCollection;
  let inputOutputSpecification;
  let loadComplete;

  function handleFormSubmit(event) {
    const formData = new FormData();
    formData.append("collection", postmanCollection.files[0]);
    formData.append("testdata", inputOutputSpecification.files[0]);

    fetch("http://localhost:5000/load", {
      method: "POST",
      body: formData
    })
      .then(response => response.text())
      .then(result => {
        loadComplete = true;
        console.log("Success:", result);
      })
      .catch(error => {
        loadComplete = false;
        console.error("Error:", error);
      });
  }
</script>

<style>
  .filepicker {
    border-radius: 0.3em;
    border-width: 0.1em;
    border-style: solid;
    border-color: black;
    width: 36em;
  }
  .center {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .check {
    border-width: 0em 0.4em 0.4em 0em;
    border-style: solid;
    border-color: green;
    height: 35px;
    width: 20px;
    margin: 3.2em 0em 0em 0em;
    transform: rotate(45deg);
    -webkit-transform: rotate(45deg);
  }
</style>

<section class="center">
  <form on:submit|preventDefault={handleFormSubmit}>
    <label for="collection">Upload Postman collection:</label>
    <input
      class="filepicker"
      id="collection"
      type="file"
      bind:this={postmanCollection} />
    <label for="testdata">Upload expected input/output specification:</label>
    <input
      class="filepicker"
      id="testdata"
      type="file"
      bind:this={inputOutputSpecification} />
    <br />
    <input class="filepicker" type="submit" />
  </form>
  {#if loadComplete}
    <div class="check" />
  {/if}

</section>

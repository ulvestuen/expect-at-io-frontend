<script>
  import { beforeUpdate } from "svelte";
  let outputDataList = updateOutputDataList();

  beforeUpdate(async () => {
    outputDataList = await updatOutputDataList();
    await new Promise(r => setTimeout(r, 1000));
  });

  let updateOutputDataList = async () => {
    const response = await fetch("http://localhost:5000/results", {
      method: "GET"
    });
    const responseJson = await response.json();
    if (response.ok) {
      return responseJson;
    }
  };
</script>

<style>
  .center {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
</style>

<section class="center">
  <pre>{JSON.stringify(outputDataList, null, '  ')}</pre>
</section>

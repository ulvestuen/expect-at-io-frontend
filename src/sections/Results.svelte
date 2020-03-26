<script>
  import { beforeUpdate } from "svelte";
  let resultList = [];
  updateResultList();

  beforeUpdate(async () => {
    updateResultList();
    await new Promise(r => setTimeout(r, 1000));
  });

  let updateResultList = async () => {
    const response = await fetch("http://localhost:5000/results", {
      method: "GET"
    });
    const responseJson = await response.json();
    if (response.ok) {
      resultList = responseJson;
    }
  };
</script>

<style>
  .center {
    display: flex;
    justify-content: center;
  }
</style>

<section class="center">
  <pre>{JSON.stringify(resultList, null, '  ')}</pre>
</section>

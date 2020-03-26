<script>
  import { beforeUpdate } from "svelte";
  let inputDataList = [];

  beforeUpdate(async () => {
    await new Promise(r => setTimeout(r, 500));
    const response = await fetch("http://localhost:5000/inputdata", {
      method: "GET"
    });
    const responseJson = await response.json();
    if (response.ok) {
      inputDataList = responseJson;
    }
  });
</script>

<style>
  .center {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .testcase {
    background-color: lightgray;
    border-style: solid;
    border-color: black;
    margin: 1em;
    padding: 1em;
  }
</style>

<section class="center">
  {#each inputDataList as inputData}
    <div class="testcase">
      <table>
        {#each Object.keys(inputData) as key}
          <tr>
            <td>
              <b>{key}</b>
            </td>
            <td>{inputData[key]}</td>
          </tr>
        {/each}
      </table>
    </div>
  {/each}
</section>

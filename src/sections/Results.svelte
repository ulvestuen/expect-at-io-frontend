<script>

    let resultList = [];
    let updateResultList = async () => {
        const response = await fetch("http://localhost:5000/results", {
            method: "GET"
        });
        const responseJson = await response.json();
        if (response.ok) {
            resultList = responseJson;
        }
    };
    updateResultList();
    setInterval(updateResultList, 2000);

</script>

<style>
    .center {
        display: flex;
        justify-content: center;
    }

    table {
        border-width: 1px;
        border-spacing: 0;
        border-style: solid;
        border-collapse: separate;
        background-color: white;
    }

    table thead td {
        border-width: 1px;
        padding: 3px;
        border-style: solid;
        border-color: gray;
        background-color: darkgray;
    }

    table tbody td {
        border-width: 1px;
        padding: 3px;
        border-style: solid;
        border-color: gray;
        background-color: lightgray;
    }

    table caption {
        caption-side: top;
        text-align: left;
    }
</style>

<section class="center">
    <table>
        <caption>Results</caption>
        <thead>
        <tr>
            <td>Test case ID</td>
            <td>Result</td>
        </tr>
        </thead>
        <tbody>
        {#each resultList as testResult}
            <tr>
                <td>{testResult.test_id}</td>
                <td>{testResult.result}</td>
            </tr>
        {/each}
        </tbody>
    </table>
</section>

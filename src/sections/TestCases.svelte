<script>
    let testCaseList = [];
    let updateTestCaseList = async () => {
        const response = await fetch("http://localhost:5000/spec/testcases", {
            method: "GET"
        });
        const responseJson = await response.json();
        if (response.ok) {
            testCaseList = responseJson;
        }
    };
    updateTestCaseList();
</script>

<style>
    .center {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: stretch;
    }

    .testcase {
        display: flex;
        flex-direction: column;
        align-items: stretch;
        background-color: white;
        border-style: solid;
        border-color: black;
        margin: 1em;
        padding: 1em;
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
    {#each testCaseList as testCase}
        <div class="testcase">
            <table>
                <caption>Test case ID</caption>
                <tbody>
                <tr>
                    <td>{testCase.id}</td>
                </tr>
                </tbody>
            </table>
            <table>
                <caption>Request</caption>
                <tbody>
                <tr>
                    <td>{testCase.request}</td>
                </tr>
                </tbody>
            </table>
            <table>
                <caption>Input</caption>
                <thead>
                <tr>
                    <td>Key</td>
                    <td>Value</td>
                </tr>
                </thead>
                <tbody>
                {#each Object.keys(testCase.input) as key}
                    <tr>
                        <td>{key}</td>
                        <td>{testCase.input[key]}</td>
                    </tr>
                {/each}
                </tbody>
            </table>
            {#each [...Array(testCase.output.length).keys()] as i}
                <table>
                    <caption>Output {i}</caption>
                    <thead>
                    <tr>
                        <td>Key</td>
                        <td>Value</td>
                    </tr>
                    </thead>
                    <tbody>
                    {#each Object.keys(testCase.output[i]) as key}
                        <tr>
                            <td>{key}</td>
                            <td>{testCase.output[i][key]}</td>
                        </tr>
                    {/each}
                    </tbody>
                </table>
            {/each}
        </div>
    {/each}
</section>

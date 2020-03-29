<script>
    let outputDataList = [];
    let updateOutputDataList = async () => {
        const response = await fetch("http://localhost:5000/spec/output", {
            method: "GET"
        });
        const responseJson = await response.json();
        if (response.ok) {
            outputDataList = responseJson;
        }
    };
    updateOutputDataList();
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

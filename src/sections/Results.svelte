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
</style>

<section class="center">
    <pre>{JSON.stringify(resultList, null, '  ')}</pre>
</section>

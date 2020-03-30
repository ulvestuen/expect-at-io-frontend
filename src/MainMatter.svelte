<script>
    export let content;
    import Load from "./sections/Load.svelte";
    import Run from "./sections/Run.svelte";
    import Results from "./sections/Results.svelte";
    import TestCases from "./sections/TestCases.svelte";
</script>

<style>

</style>

{#if content === 'Load'}
    <Load/>
{/if}
{#if content === 'TestCases'}
    <TestCases/>
{/if}
{#if content === 'Run'}
    <Run/>
{/if}
{#if content === 'Results'}
    <Results/>
{/if}

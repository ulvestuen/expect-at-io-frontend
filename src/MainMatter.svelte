<script>
    export let content;
    import Load from "./sections/Load.svelte";
    import Input from "./sections/Input.svelte";
    import Output from "./sections/Output.svelte";
    import Run from "./sections/Run.svelte";
    import Results from "./sections/Results.svelte";
</script>

<style>

</style>

{#if content === 'Load'}
    <Load/>
{/if}
{#if content === 'Input'}
    <Input/>
{/if}
{#if content === 'Output'}
    <Output/>
{/if}
{#if content === 'Run'}
    <Run/>
{/if}
{#if content === 'Results'}
    <Results/>
{/if}

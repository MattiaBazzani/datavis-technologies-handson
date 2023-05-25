<script>
    import { json } from "d3-fetch";
    import {onMount} from "svelte";
    import Scatterplot from "./Scatterplot.svelte";
    let data = null;
    onMount(async () => {
        console.log("onMount started!");
        data = await json('/static/data/gapminder.json');
        console.log("Data loaded!");
    });
    console.log("Script finished!")
</script>

{#if !data}
    <p> loading the data, please wait...</p>
{:else}
    <Scatterplot data={data[0]["countries"]} />
{/if}

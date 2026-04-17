<script>
    import { base } from "$app/paths";
    export let data = {};
</script>

<article>
    <h2>{data.title}</h2>
    {#if data.url}
        <a href={data.url.startsWith("http") ? data.url : base+data.url}><img src={data.image} alt=""></a>
    {:else}
        <img src={data.image} alt="">
    {/if}
    <p><strong>{data.year} |</strong> {data.description}</p>
</article>

<style>
    img {
        max-width: 100%;
    }

    h2 {
        margin: 0;
    }

    article {
        display: grid;
        grid-template-rows: subgrid;
        grid-row: span 3;
    }
</style>

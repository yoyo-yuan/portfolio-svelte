<script>
    import { base } from "$app/paths";
    export let data = {};
</script>

<article>
    <h2>{data.title}</h2>
    <a href={data.url.startsWith("http") ? data.url : base+data.url}><img src={data.image} alt=""></a>
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

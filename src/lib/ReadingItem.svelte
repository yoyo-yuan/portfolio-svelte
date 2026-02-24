<script>
    export let data = {};
</script>

<article>
    <img src={data.image} alt="">
    <div class="info">
        <strong>{data.title}</strong>
        <p>{data.author}</p>
    </div>
</article>

<style>
    img {
        max-width: 6rem;
    }

    strong {
        margin: 0;
    }

    article {
        display: grid;
        grid-template-columns: auto minmax(105px, 1fr);
        grid-row: span 3;
        align-items: center;
        gap: 1rem;
        margin-bottom: 1rem;
    }

    .info {
        display: flex;
        flex-direction: column;
    }
</style>

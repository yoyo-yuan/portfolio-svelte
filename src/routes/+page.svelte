<script>
    import projects from "$lib/projects.json";
    import reading from "$lib/reading.json";
    import Project from "$lib/Project.svelte";
    import ReadingItem from "$lib/ReadingItem.svelte";
    import { onMount } from "svelte";

    let sorted_projects = projects.sort((a, b) => b.year - a.year);
    let githubData = null; // This will eventually hold our Github stats
    let loading = true; // This will be true *until* the fetch's promise resolves to a value
    let error = null; // If the API call resulted in an error, it will go into this variable
    onMount(async () => {
        try {
            console.log("Page has been mounted!")
            let response = await fetch("https://api.github.com/users/yoyo-yuan");
            console.log(response);
            githubData = await response.json();
            console.log(githubData);
        } catch (err) {
            error = err;
        }
        loading = false;
    });
</script>

<svelte:head>
    <title>Yoyo Yuan: Personal site and portfolio</title>
</svelte:head>

<div class="aboutMe">
    <div class="intro">
        <h1>Yoyo Yuan</h1>
        <p>
            Hi! I’m a sophomore at MIT majoring in Computer Science and Mathematics. I have experience in
            software engineering, financial advisory, and quantitative trading. On campus, I serve as Banana
            Lead of the MIT Banana Lounge and as Room Assignment Chair in Maseeh Hall. I’m excited to continue
            exploring opportunities at the intersection of technology and finance.
        </p>
        <img src="images/Headshot_Yoyo Yuan.jpg" alt="A headshot of me!" />
    </div>
    <div class="currentReading">
        <h2>What I'm Reading</h2>
        <div class="reading">
            {#each reading as r}
                <ReadingItem data={r} />
            {/each}
        </div>
    </div>
</div>

{#if loading}
    <p>Loading...</p>
{:else if error}
    <p>Something went wrong: {error.message}</p>
{:else}
    <section>
        <h2>My GitHub Stats</h2>
        <dl>
            <dt>Followers</dt>
            <dd>{githubData.followers}</dd>
            <dt>Following</dt>
            <dd>{githubData.following}</dd>
            <dt>Public Repositories</dt>
            <dd>{githubData.public_repos}</dd>
        </dl>
    </section>
{/if}

<h2>Latest projects</h2>
<div class="projects">
	{#each sorted_projects.slice(0, 3) as p}
        <Project data={p} />
    {/each}
</div>

<style>
    dl {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-auto-flow: column;
        align-items: start;
        margin-bottom: 3rem;
    }

    dl > dt {
        grid-row: 1;
        text-transform: uppercase;
        font-size: 1rem;
        color: gray;
    }

    dl > dd {
        grid-row: 2;
        font-size: 2rem;
        line-height: 1;
        font-weight: 150;
    }
</style>

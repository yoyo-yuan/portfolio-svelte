<script>
  import projects from "$lib/projects.json";
  import reading from "$lib/reading.json";
  import Project from "$lib/Project.svelte";
  import ReadingItem from "$lib/ReadingItem.svelte";
</script>

<nav>
    <a href="." class="current">Home</a>
    <a href="projects">Projects</a>
    <a href="contact">Contact</a>
    <a href="resume">Resume</a>
    <a href="https://github.com/yoyo-yuan" target="_blank">GitHub</a>
</nav>
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

<h2>Latest projects</h2>
<div class="projects">
	{#each projects.slice(0, 3) as p}
        <Project data={p} />
    {/each}
</div>

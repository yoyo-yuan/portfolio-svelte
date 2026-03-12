<script>
    import projects from "$lib/projects.json";
    import Project from "$lib/Project.svelte";
    import ProjectNarrative from "$lib/ProjectNarrative.svelte";
    import Bar from '$lib/Bar.svelte';

    let sorted_projects = projects.sort((a, b) => a.year - b.year);
    let years = projects.map(proj => proj.year);
    let range = Math.max(...years) - Math.min(...years);

    import { onMount } from 'svelte';
    import * as d3 from 'd3';
    let rawData = [];
    let wrangled = [];
    onMount(async () => {
        rawData = await d3.json('/lab6_example.json');
        const total = d3.sum(rawData, d => d.lines);
        wrangled = d3.rollups(
            rawData,
            v => d3.sum(v, d => d.lines)/total * 100,
            d => d.language
        );
    });
    $: barData = d3.rollups(sorted_projects, v => v.length, d => d.year)
        .map(([year, count]) => ({ label: String(year), value: count }));
</script>

<svelte:head>
    <title>Projects</title>
</svelte:head>

<h1>{ projects.length } Projects over {range} Years</h1>
<Bar data={barData} />
<p>
    Scroll down to see my a timeline of my projects and how they've contributed to my professional and personal life
</p>
<ProjectNarrative />
<p class="outro">
    Thanks for scrolling through my project story! Feel free to explore all of the projects at your leisure below.
</p>

<div class="projects">
	{#each projects as p}
		<Project data={p} />
	{/each}
</div>

<style>
    .outro {
        margin-bottom: 5rem;
    }
</style>

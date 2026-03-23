<script>
    import { base } from '$app/paths';
    import { onMount, tick } from 'svelte';
    import * as d3 from 'd3';
    import BarHorizontal from '../../lib/BarHorizontal.svelte';
    import {
        computePosition,
        autoPlacement,
        offset,
    } from '@floating-ui/dom';

    let locData = [];
    let commits = [];
    onMount(async () => {
        locData = await d3.csv(`${base}/loc.csv`, row => ({
            ...row,
            line: Number(row.line),
            length: Number(row.length),
            depth: Number(row.depth),
            date: new Date(row.date + "T00:00" + row.timezone),
            datetime: new Date(row.datetime)
        }));
        commits = d3.groups(locData, d => d.commit).map(([commit, lines]) => {
            let first = lines[0];
            let {author, date, time, timezone, datetime} = first;
            let ret = {
                id: commit,
                url: "https://github.com/yoyo-yuan/portfolio-svelte/commit/" + commit,
                author, date, time, timezone, datetime,
                hourFrac: datetime.getHours() + datetime.getMinutes() / 60,
                totalLines: lines.length,
                lines: lines
            };
            return ret;
        });
        commits = d3.sort(commits, d => -d.totalLines);
    });
    $: selectedLines = (clickedCommits.length > 0 ? clickedCommits.flatMap(d => d.lines) : locData);
    $: selectedCounts = d3.rollup(
        selectedLines,
        v => v.length,
        d => d.type
    );
    $: allTypes = Array.from(new Set(locData.map(d => d.type)));
    $: barData = allTypes.map(type =>  ({ label: String(type), value: selectedCounts.get(type) || 0 }));

    let width = 1000, height = 600;
    let margin = { top: 40, right: 60, bottom: 40, left: 60 };
    let usableArea = {
        top: margin.top,
        right: width - margin.right,
        bottom: height - margin.bottom,
        left: margin.left
    };
    usableArea.width = usableArea.right - usableArea.left;
    usableArea.height = usableArea.bottom - usableArea.top;

    $: [minDate, maxDate] = d3.extent(commits.map(d => d.date));
    $: maxDatePlusOne = new Date(maxDate);
    $: maxDatePlusOne.setDate(maxDatePlusOne.getDate() + 1);
    $: xScale = d3.scaleTime()
                .domain([minDate, maxDatePlusOne])
                .range([usableArea.left, usableArea.right])
                .nice();
    $: yScale = d3.scaleLinear()
                .domain([24, 0])
                .range([usableArea.bottom, usableArea.top]);

    let xAxis, yAxis, yAxisGridlines;
    $: {
        d3.select(xAxis).call(d3.axisBottom(xScale));
        d3.select(yAxis).call(d3.axisLeft(yScale).tickFormat(d => String(d % 24).padStart(2, "0") + ":00"));
        d3.select(yAxisGridlines).call(
            d3.axisLeft(yScale)
            .tickFormat("")
            .tickSize(-usableArea.width)
        );
    }

    $: [minLines, maxLines] = d3.extent(commits, d => d.totalLines);
    $: rScale = d3.scaleSqrt()
        .domain([minLines, maxLines])
        .range([5, 30]);

    let hoveredIndex = -1;
    $: hoveredCommit = commits[hoveredIndex] ?? hoveredCommit ?? {};
    let commitTooltip;
    let tooltipPosition = {x: 0, y: 0};
    let clickedCommits = [];
    async function dotInteraction (index, evt) {
        let hoveredDot = evt.target;
        if (evt.type === "mouseenter") {
            hoveredIndex = index;
            tooltipPosition = await computePosition(hoveredDot, commitTooltip, {
                strategy: "fixed", // because we use position: fixed
                middleware: [
                    offset(5), // spacing from tooltip to dot
                    autoPlacement() // see https://floating-ui.com/docs/autoplacement
                ],
            });
        }
        else if (evt.type === "mouseleave") {
            hoveredIndex = -1
        }
        else if (evt.type === "click") {
            let commit = commits[index]
            if (!clickedCommits.includes(commit)) {
                // Add the commit to the clickedCommits array
                clickedCommits = [...clickedCommits, commit];
            }
            else {
                // Remove the commit from the array
                clickedCommits = clickedCommits.filter(c => c !== commit);
            }
        }
    }
</script>

<svelte:head>
    <title>Meta</title>
</svelte:head>


<h1>Meta</h1>
<p>
    Meta page to visualize project data.
</p>

<dl
    class="info tooltip"
    hidden={hoveredIndex === -1}
    bind:this={commitTooltip}
    style="top: {tooltipPosition.y}px; left: {tooltipPosition.x}px"
>
    <dt>Commit</dt>
    <dd><a href={ hoveredCommit.url } target="_blank">{ hoveredCommit.id }</a></dd>

    <dt>Author</dt>
    <dd>{ hoveredCommit.author }</dd>

    <dt>Date</dt>
    <dd>{ hoveredCommit.datetime?.toLocaleString("en", {dateStyle: "full"}) }</dd>

    <dt>Time</dt>
    <dd>{ hoveredCommit.datetime?.toLocaleString("en", {timeStyle: "short"}) }</dd>

    <dt>Lines edited</dt>
    <dd>{ hoveredCommit.totalLines }</dd>
</dl>
<svg viewBox="0 0 {width} {height}">
    <text
        x={width / 2}
        y={margin.top / 2}
        text-anchor="middle"
        class="chart-title">
        Commits by Time of Day
    </text>
    <g transform="translate(0, {usableArea.bottom})" bind:this={xAxis} />
    <g class="gridlines" transform="translate({usableArea.left}, 0)" bind:this={yAxisGridlines} />
    <g transform="translate({usableArea.left}, 0)" bind:this={yAxis} />
    <g class="dots">
        {#each commits as commit, index }
            <circle
                class:selected={ clickedCommits.includes(commit) }
                on:click={ evt => dotInteraction(index, evt) }
                on:mouseenter={evt => dotInteraction(index, evt)}
	            on:mouseleave={evt => dotInteraction(index, evt)}
                cx={ xScale(commit.datetime) }
                cy={ yScale(commit.hourFrac) }
                r={ rScale(commit.totalLines) }
                fill="steelblue"
            />
        {/each}
    </g>
</svg>

<BarHorizontal data={barData} title = {clickedCommits.length == 0 ? "Website Breakdown" : "Selected Commits"}/>


<style>
	svg {
		overflow: visible;
	}

    .gridlines {
        stroke-opacity: .2;
    }

    .dots {
        fill-opacity: .7;
    }

    circle {
        transition: 200ms;
        &:hover {
            fill:darkgreen;
        }
    }

    dl.info {
        display: grid;
        grid-template-columns: max-content 1fr;
        gap: 0.25em 0.75em;
        transition-duration: 500ms;
        transition-property: opacity, visibility;
        &[hidden]:not(:hover, :focus-within) {
            opacity: 0;
            visibility: hidden;
	    }
    }

    .info dt {
        margin: 0;
        font-weight: 600;
        color: rgb(0, 0, 0, 0.5);
        text-transform: uppercase;
    }

    .info dd {
        margin: 0;
    }

    .tooltip {
        position: fixed;
        top: 1em;
        left: 1em;
        padding: 1.5em 1.5em;
        background-color: oklch(100% 0% 0 / 80%);
        box-shadow: 1px 1px 3px 3px rgb(0, 0, 0, 0.3);
        border-radius: 5px;
        backdrop-filter: blur(5px);
    }

    .selected {
        fill: var(--color-accent);
    }

    .chart-title {
        font-size: 30px;
        font-weight: bold;
        fill: currentColor;
    }
</style>

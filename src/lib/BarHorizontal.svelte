<script>
    import * as d3 from 'd3';
    let width = 500;
    let height = 300;
    export let data = [];

    let margin = { top: 40, right: 20, bottom: 40, left: 80 };;
    let innerWidth  = width  - margin.left - margin.right;
    let innerHeight = height - margin.top  - margin.bottom;
    $: xScale = d3.scaleLinear()
        .domain([0, d3.max(data, d => d.value) || 1])
        .range([0, innerWidth]);

    $: yScale = d3.scaleBand()
        .domain(data.map(d => d.label))
        .range([0, innerHeight])
        .padding(0.2);

    $: colorScale = d3.scaleOrdinal(d3.schemePastel1)
        .domain(data.map(d => d.label));

    let xAxis, yAxis;
    $: if (xAxis && yAxis) {
        d3.select(xAxis).call(
            d3.axisBottom(xScale)
                .tickFormat(d => Number.isInteger(d) ? d : "")
        );
        d3.select(yAxis).call(d3.axisLeft(yScale));
    }

    $: maxBar = d3.greatest(data, d => d.value);
</script>

<div class="container">
    <svg viewBox="0 0 {width} {height}">
        <!-- chart title -->
        <text
            x={margin.left + innerWidth / 2}
            y={margin.top / 2}
            text-anchor="middle"
            class="chart-title">
            Lines of Code by Language
        </text>
        <g transform="translate({margin.left}, {margin.top + innerHeight})"
        bind:this={xAxis} />
        <g transform="translate({margin.left}, {margin.top})"
        bind:this={yAxis} />
        <g transform="translate({margin.left}, {margin.top})">
            <!-- x-axis label -->
            <text
                x={innerWidth / 2}
                y={innerHeight + margin.bottom + 3}
                text-anchor="middle"
                class="axis-label">
                Lines of Code
            </text>
            <!-- y-axis label -->
            <text
                x={-(innerHeight / 2)}
                y={-margin.left + 30}
                text-anchor="middle"
                transform="rotate(-90)"
                class="axis-label">
                Programming Language
            </text>
        </g>
        <g transform="translate({margin.left}, {margin.top})">
            {#each data as d}
                <rect
                    x={0}
                    y={yScale(d.label)}
                    width={xScale(d.value)}
                    height={yScale.bandwidth()}
                    fill={colorScale(d.label)}
                />
            {/each}
            {#if maxBar}
                <!-- highlight outline around the tallest bar -->
                <rect
                    x={0}
                    y={yScale(maxBar.label)}
                    width={xScale(maxBar.value)}
                    height={yScale.bandwidth()}
                    fill="none"
                    stroke="currentColor"
                    stroke-width="2"
                />
                <!-- leader line -->
                <line
                    x1={xScale(maxBar.value) / 2}
                    y1={yScale(maxBar.label) + yScale.bandwidth()}
                    x2={xScale(maxBar.value) / 2}
                    y2={yScale(maxBar.label) + yScale.bandwidth() + 30}
                    stroke="currentColor"
                    stroke-width="1"
                />
                <!-- annotation text at end of leader line -->
                <text
                    x={xScale(maxBar.value) / 2}
                    y={yScale(maxBar.label) + yScale.bandwidth() + 45}
                    text-anchor="middle"
                    class="annotation">
                    Most lines of code
                </text>
            {/if}
        </g>
    </svg>
    <ul class="legend">
        {#each data as d}
            <li style="--color: {colorScale(d.label)}">
                <span class="swatch"></span>
                {d.label} <em>({d.value})</em>
            </li>
        {/each}
    </ul>
</div>

<style>
    svg {
        max-width: 100%;
        height: auto;
        overflow: visible;
    }

    .container {
        display: flex;
        align-items: center;
    }

    .legend {
        flex: 1;
    }

    .swatch {
        width: 12px;
        height: 12px;
        background-color: var(--color);
        display: inline-block;
    }

    li {
        display: flex;
        align-items: center;
        gap: 0.5rem;
    }

    .chart-title {
        font-size: 1em;
        font-weight: bold;
        fill: currentColor;
    }

    .axis-label {
        font-size: 0.8em;
        fill: gray;
    }

    .annotation {
        font-size: 0.7em;
        fill: black;
        font-style: italic;
    }
</style>

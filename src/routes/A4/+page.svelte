<svelte:head>
    <title>Vis & Society Assignment 4</title>
	<link rel="stylesheet" href="https://vis-society.github.io/assignments/report.css" />
</svelte:head>

<div class="A4_report">
    <header>
		<h1>
			<small>Assignment 4</small>
			Persuasive or Deceptive Visualization?
		</h1>

		<p>
			<strong>Yoyo Yuan</strong> — <em>yyyuan@mit.edu</em>
		</p>
	</header>

	<main>
    <h2>Proposition: Investigations increasingly confirm incidents described in NYPD civilian complaints.</h2>

		<section>
      <h3>FOR the Proposition</h3>

      <figure>
				<img src="images/A4/For the Proposition Visualization.png" alt="Investigations Are Confirming More NYPD Civilian Complaints Over Time" />
				<figcaption>
					Percentage of NYPD civilian complaints by investigation outcome from 1985 to 2019, showing the growing proportion of
					confirmed incidents (substantiated and exonerated).
				</figcaption>
			</figure>

			<p>
				Design Decisions and Rationale:
			</p>

			<ul>
				<li>
					<strong>[Score: 1]</strong> I used a 100% stacked area chart to illustrate changes in the percentage of complaints
					across the three board dispositions from 1985 to 2019. Before settling on this chart type, I explored several
					alternatives, including line graphs, stacked bar charts, and stacked area plots. I ultimately chose this style because
					it provides a clear way for readers to perceive the relative relationship between the three dispositions and observe
					the increasing share of confirmed incidents, represented by the substantiated and exonerated categories. One drawback
					of this visualization is that it sacrifices information about the absolute number of complaints. However, it emphasizes
					the changing share of civilian complaint outcomes in a more striking and visually impactful way.
				</li>
				<li>
					<strong>[Score: 1]</strong> I highlighted the substantiated and exonerated categories with bright, vibrant colors to
					draw the readers’ attention. I used a more alarming red for substantiated cases, which represent incidents where the
					alleged conduct occurred and violated department rules. For exonerated cases, which indicate that the alleged conduct
					occurred but did not violate rules, I used an orange color that conveys a sense of warning but appears less severe
					than red. In contrast, I used a muted gray for the unsubstantiated category to downplay its visual prominence. This
					choice pushes the category into the background and helps keep the viewer’s attention on the categories I intend to
					emphasize.
				</li>
				<li>
					<strong>[Score: -1]</strong> I experimented with the stacking order of the three categories. Initially, I placed the
					substantiated category at the bottom of the chart because it represents the most severe outcome. However, the
					percentage of substantiated cases only increased slightly over the time period. Therefore, I moved it above the
					exonerated category, which shows a stronger increase. Since only the bottom category shares a consistent baseline at
					zero, this arrangement makes the upward trend in the exonerated category more visually prominent, causing the combined
					area of the two categories to appear to increase more strongly.
				</li>
				<li>
					<strong>[Score: 2]</strong> I excluded data from 2020. The dataset only contains records from September 1985 through
					January 2020, meaning the 2020 data represents only a very small portion of the year. Including these incomplete data
					points could create a misleading impression of trends in 2020. Removing them ensures that each year shown in the
					visualization represents a full and comparable period.
				</li>
				<li>
					<strong>[Score: 1]</strong> I colored the visualization title with a hue between the red and orange used for the
					substantiated and exonerated categories. This design choice subtly aligns the title with the colors of the emphasized
					categories, which may subconsciously guide the reader’s attention toward them. However, the vibrant color choice may
					feel somewhat intentional to attentive viewers.
				</li>
			</ul>
    </section>

    <section>
      <h3>AGAINST the Proposition</h3>

      <figure>
				<img src="images/A4/Against the Proposition Visualization.png" alt="Unsubstantiated Complaints Dominate NYPD Investigation Outcomes Over Time" />
				<figcaption>
					Number of NYPD civilian complaints by investigation outcome over time, highlighting the increasing number of
					unsubstantiated complaints.
				</figcaption>
			</figure>

			<p>
				Design Decisions and Rationale:
			</p>

			<ul>
				<li>
					<strong>[Score: 2]</strong> I used a line graph to illustrate changes in the number of civilian complaints in each
					disposition category over time, overlaid on top of a bar chart showing the total number of complaints each year. This
					design was inspired by the lollipop chart, which overlays a dot plot on a bar chart. However, I chose a line graph
					because it conveys changes over time in a more straightforward way and allows readers to easily perceive shifts across
					years. The bar chart in the background provides context by showing the absolute magnitude of total complaints each
					year, enabling readers to interpret both the raw counts of each category and their relationship to the total number.
				</li>
				<li>
					<strong>[Score: 2]</strong> In this visualization, I colored the three disposition categories using vibrant colors
					to emphasize the seriousness of the issue. Unsubstantiated complaints, which indicate that investigations could not
					conclude that the alleged conduct occurred, are shown in bright red to attract the audience’s attention since they
					are the focus of this visualization. The other two categories are colored to reflect the severity of the investigation
					outcome: the exonerated category, where the alleged conduct occurred but did not violate department rules, is shown
					in orange, while the substantiated category, where the conduct both occurred and violated rules, is colored yellow.
					This color scheme communicates a conceptual progression among the board dispositions while maintaining visual
					distinction. The bar chart uses a muted gray color because it mainly serves as contextual information and should
					not visually compete with the key categories represented by the line graph.
				</li>
				<li>
					<strong>[Score: -1]</strong> I further emphasized the unsubstantiated line by adjusting the line thickness according
					to the number of unsubstantiated complaints. As the counts increase, the line becomes thicker and creates stronger
					visual dominance, making the increase appear more dramatic. In contrast, the substantiated and exonerated lines
					remain thin throughout. This design choice reduces their visual presence and causes the audience to focus primarily
					on the unsubstantiated trend, overshadowing the other categories.
				</li>
				<li>
					<strong>[Score: -2]</strong> I truncated the dataset to include only 1985–2014 in this visualization since the full
					dataset shows a noticeable drop in the number of unsubstantiated complaints from 2014 to 2019. Although the broader
					trend still shows an overall increase, the decline in the later years could weaken the argument and prompt viewers
					to question the narrative. By excluding those years, I was able to present a more consistent upward trend that
					strengthens the intended message.
				</li>
				<li>
					<strong>[Score: 1]</strong> I colored the visualization title using a red hue that matches the line color for the
					unsubstantiated category. This design choice subtly aligns the title with the category in focus and may
					subconsciously guide readers’ attention toward it. However, the strong color choice may also appear intentional to
					attentive viewers.
				</li>
			</ul>
    </section>

    <section>
      	<h2>Final Reflection</h2>

      	<p>
			The design process for this assignment was both engaging and challenging because it asked me to explore different
			perspectives using the same dataset. At first, I found the process overwhelming because the dataset contained many variables
			and possible directions for analysis, making it difficult to choose which ones would best support two opposing claims.
			Selecting appropriate data transformations was particularly challenging because I had to balance emphasizing the central
			claim without becoming overly deceptive. For example, I considered applying a logarithmic scale to the y-axis of the line
			graph. This transformation would have emphasized early increases while compressing later changes, which could downplay the
			decline in the final years of the dataset. Although this choice could strengthen the intended message, I decided against it
			because it could make the visualization harder to interpret and potentially mislead readers. In contrast, some design choices,
			such as color and line thickness, were more intuitive because viewers naturally focus on brighter colors and thicker marks,
			while muted colors and thinner lines tend to fade into the background.
	  	</p>
		<p>
			Through this process, I realized that the boundary between ethical and unethical visualization designs can be difficult to
			define. Designers can technically present the full dataset while still making certain elements less noticeable through color,
			size, or placement. In these cases, the information is present, but viewers may be less likely to focus on it. I believe
			ethical visualizations should make important information clearly visible so readers can interpret the data themselves, even
			if design choices guide attention toward particular aspects of it. This assignment showed me how powerful design choices can
			be: small alterations in design decisions can lead to very different interpretations and even support opposing narratives
			using the same dataset. It was surprising to see how strongly visualizations alone can communicate a viewpoint, even without
			much text.
		</p>
    </section>
	</main>
</div>

<style>
    .A4_report {
        width: 110ch;
        position: relative;
        left: 50%;
        transform: translateX(-50%);
    }
</style>

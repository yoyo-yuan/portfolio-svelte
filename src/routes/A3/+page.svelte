<svelte:head>
    <title>Vis & Society Assignment 3</title>
	<link rel="stylesheet" href="https://vis-society.github.io/assignments/report.css" />
</svelte:head>

<div class="A3_report">
	<header>
		<h1>
			<small>Assignment 3</small>
			Visualization Critique & Redesign
		</h1>

		<p>
			<strong>Yoyo Yuan</strong> — <em>yyyuan@mit.edu</em>
		</p>
	</header>

	<main>
		<section>
			<h2>Reading & Critique</h2>

			<figure>
				<img src="https://vis-society.github.io/assets/imgs/covid-spiral.png" alt="" />
			</figure>

			<p>
				Insights about the data/visualization:
			</p>

			<ul>
				<li>
					The visualization covers data from March 2020 through January 2022, arranged in a
					spiral format where each loop represents a calendar year. Earlier data begin near
					the center and gradually expand outward over time, with the outermost section representing
					the most recent data before the article’s publication.
				</li>
				<li>
					Each successive spiral appears wider at its peaks, indicating an increase in the number of
					new Covid-19 cases in the U.S over time. In particular, the January 2022 segment shows a
					dramatic increase in width that far exceeds previous peaks, visually emphasizing the
					unprecedented surge associated with the Omicron variant.
				</li>
				<li>
					The spiral layout reveals a recurring seasonal pattern: case counts generally decline in
					the spring and summer, especially from May through July, and rise again in the fall and winter,
					approximately from November through February.
				</li>
			</ul>

			<p>
				Design Critique:
			</p>

			<p>
				The visualization conveys the data in a creative and largely effective way. The unique spiral
				layout and alarming red color immediately capture attention, serving its purpose well as an
				article opener. The bold color choice reinforces the urgency of the situation at the time of
				publication, when case counts were rising dramatically. The circular axis works well conceptually
				since months repeat each year, allowing readers to compare similar months across different years
				and making seasonal patterns more noticeable. Rather than using layered concentric circles, the
				continuous spiral emphasizes temporal continuity and reduces the need for readers to shift their
				attention between separate panels or estimate relative magnitudes across disjointed plots. The axes
				and width legend are labeled, the title clearly communicates the topic, and the minimalist design
				leaves ample white space that directs attention to the data itself. Expanding the band symmetrically
				around a central line further highlights the stark differences between lower and higher case counts.
				Overall, the visual design choices are simple yet powerful.
			</p>
			<p>
				However, the visualization also obscures certain important aspects of the data. Most notably, it
				makes it difficult to interpret absolute magnitudes. Although a scale reference is provided, it is
				positioned separately from the spiral, requiring readers to visually estimate widths and mentally
				map them to the legend. This indirect comparison reduces precision and may weaken readers’ confidence
				in data accuracy. Additionally, because the spiral expands outward over time, more recent data are
				positioned farther from the center. This spatial arrangement may unintentionally lead readers to
				perceive recent values as larger at first glance simply due to their outward position, even though
				magnitude is encoded through band thickness rather than radial distance. Furthermore, while the
				circular axis begins in January to align with common expectations about the calendar year, the data
				itself starts in March 2020. The absence of the red band in January and February is not explicitly
				labelled, which may create confusion or imply that cases only began in March. While the visualization
				succeeds as an attention-grabbing and conceptually engaging opener, these design choices introduce
				ambiguities that could be addressed to improve clarity, accuracy, and interpretability.
			</p>
		</section>

		<section>
			<h2>Visualization Sketches</h2>

      <figure>
				<img src="images/A3/6.C35 A3 Sketch 1.jpg" alt="Sketch 1" />
				<figcaption>
					Cartesian line graph with seasonal segmentation
				</figcaption>
			</figure>

			<p>
				Design Rationale for Sketch 1:
			</p>

			<ul>
				<li>
					I chose a Cartesian line graph to address the original visualization’s lack of clear information
					on absolute magnitude. Since all lines share a common zero baseline and are encoded with vertical
					position along the y-axis, the chart also provides more precise positional comparisons across years.
				</li>
				<li>
					I kept the red color for 2022 to emphasize the severity of the most recent surge. To distinguish
					earlier years, I used green for 2020 to represent the initial emergence and relatively low case counts,
					and yellow for 2021 to suggest escalation leading into the peak in 2022.
				</li>
				<li>
					I divided the x-axis into seasonal segments and labelled them clearly to bring attention to the recurring
					seasonal patterns without sacrificing magnitude clarity.
				</li>
				<li>
					This visualization more effectively communicates both relative and absolute differences in new COVID-19
					case counts in the U.S. The use of lines also ensures that trends remain legible when multiple years
					are displayed together.
				</li>
				<li>
					However, the linear structure leads to discontinuity between years since each year is plotted separately
					along the x-axis. Readers must shift their focus from the end of one year to the beginning of the next,
					interrupting trends that continue over years.
				</li>
				<li>
					In the next sketch, I aim to reintroduce a circular month structure while maintaining a shared zero
					baseline, balancing a cyclical context with an accurate magnitude representation.
				</li>
			</ul>

			<figure>
				<img src="images/A3/6.C35 A3 Sketch 2.jpg" alt="Sketch 2" />
				<figcaption>
					Circular line graph with a continuous timeline
				</figcaption>
			</figure>

			<p>
				Design Rationale for Sketch 2:
			</p>

			<ul>
				<li>
					In this sketch, I combined elements from my first sketch and the original New York Times visualization.
					I chose a circular line graph because it communicates precise positional information about both absolute
					and relative magnitudes, while the circular axis restores temporal continuity by directly connecting
					December of one year to January of the next.
				</li>
				<li>
					I kept the green, yellow, and red color scheme to represent 2020, 2021, and 2022 respectively. Since the
					line now flows continuously across years, color becomes essential for distinguishing annual segments and
					preventing confusion between different time periods.
				</li>
				<li>
					I added explicit annotations marking the start and end dates of the dataset to address the ambiguity
					identified in my critique of the original visualization. This clarification prevents misinterpretation
					about when U.S. COVID-19 cases began appearing in the data.
				</li>
				<li>
					This design aims to preserve the cyclical structure of months while enabling clearer monthly comparisons
					across years. By maintaining a shared zero baseline at the center, the visualization communicates absolute
					magnitude more effectively than the original spiral. The temporal continuity in this visualization also
					allows readers to trace trends across years without the interruption introduced by a linear x-axis.
				</li>
				<li>
					However, this design introduces new challenges. Small values are compressed toward the center of the circle,
					where available space is limited, making small differences difficult to perceive. Overlapping lines near
					the center are also harder to distinguish. Additionally, because all years now occupy the same radial space,
					the chart can feel visually crowded, making it challenging to focus on a single year. Unlike the original
					spiral, which used expanding width to create strong shape contrast, this design relies solely on radial
					position, which may seem less dramatic to readers.
				</li>
				<li>
					In the next sketch, I aim to improve the perceptibility of smaller values while maintaining the cyclical
					month structure. I also plan to incorporate design elements that more cohesively reflect the subject.
				</li>
			</ul>

			<figure>
				<img src="images/A3/6.C35 A3 Sketch 3.jpg" alt="Sketch 3" />
				<figcaption>
					Spherical tally-based visualization resembling the Omicron variant
				</figcaption>
			</figure>

			<p>
				Design Rationale for Sketch 3:
			</p>

			<ul>
				<li>
					While maintaining the circular structure to preserve temporal continuity, I expanded the design into
					a three-dimensional sphere. The circumference is divided into twelve segments representing months, and
					the radial dimension is separated into three concentric rings representing 2020, 2021, and 2022. The
					outward expansion of rings for more recent years metaphorically reflects the increasing scale of viral
					spread over time.
				</li>
				<li>
					I represented case counts using a tallying method, where red triangular bumps resembling the spikes
					of the Omicron variant form the surface texture of the sphere. The thickness and density of these
					tallies vary to indicate smaller versus larger case counts. This visual encoding choice makes the
					entire sphere resemble the virus itself.
				</li>
				<li>
					The visualization is designed to capture attention and communicate the subject matter immediately.
					The dominant red color reinforces the severity of the pandemic, while the spherical virus-like
					layout strengthens the plot’s coherence with the subject. The number, density, and thickness of
					tallies aim to communicate both absolute magnitude through counting and relative magnitude through
					visual crowding and thickness.
				</li>
				<li>
					The unconventional layout and symbolic design elements effectively serve the original visualization’s
					purpose as an attention-grabbing article opener. Variations in tally density across months visually
					suggest increases and decreases in case counts, helping readers infer seasonal patterns.
				</li>
				<li>
					However, this design also introduces interpretability challenges. Although tallies theoretically
					encode exact numerical values, readers would need to manually count and sum them to determine
					monthly totals, which is impractical. Additionally, while December and January are positioned near
					each other, they remain separated by different yearly rings, limiting direct cross-year comparison.
					Finally, the unusual structure and visual encoding may require readers to spend more time decoding
					the design elements before extracting meaningful insights.
				</li>
				<li>
					In the final visualization, I aim to synthesize insights from these sketches to develop a design
					that balances their respective strengths and limitations.
				</li>
			</ul>
		</section>

		<section>
			<h2>Final Visualization Design</h2>

			<figure>
				<img src="images/A3/6.C35 A3 Final Visualization.png" alt="Final Visualization" />
				<figcaption>
					Stacked polar area chart with a circular month axis and concentric yearly layers
				</figcaption>
			</figure>

		</section>

		<section>
			<h2>Final Writeup</h2>

			<p>
				My final visualization aims to accurately communicate the number of new COVID-19 cases per month while
				enabling temporal comparisons across adjacent months, the same month in different years, and transitions
				between years. To maintain the seasonal continuity emphasized in the original visualization, I preserved
				the radial layout but introduced a clearly labeled axis to improve access to absolute magnitude. When
				constructing the visualization, I excluded an unreasonable data point in December 2022 with a negative
				case count and ordered the years radially so that earlier years begin near the center and extend outward,
				reinforcing chronological progression. I adopted a green-yellow-red color scheme to represent 2020, 2021,
				and 2022 respectively, reflecting the initial emergence of cases, subsequent instability, and the drastic
				surge in early 2022. I chose a stacked polar area chart rather than a line graph to reduce visual
				interference between overlapping years and provide a more immediate impression of relative magnitude
				through filled shapes. To address congestion near the center identified in earlier sketches, I adjusted
				the radial scaling to expand smaller values and compress larger ones while clearly annotating the axis.
			</p>

			<p>
				This design addresses several critiques of the original visualization, particularly the difficulty of
				interpreting absolute magnitude from band width alone. By overlaying values against a visible axis, the
				chart improves magnitude readability while preserving cyclical structure and seasonal patterns. I also
				added explicit annotations marking the start and end dates of the graphed data to clarify the temporal
				scope and eliminate the ambiguity present in the original visualization. However, the stacked structure
				introduces tradeoffs: extracting exact yearly values requires subtracting inner layers, and stacking
				unintentionally draws attention to cumulative totals that are not analytically meaningful. Through the
				critique-by-redesign process, I recognized the tension between precision and readability. A shared zero
				baseline maximize numerical accuracy but create clutter, whereas separation and stacking improve clarity
				but reduce exact interpretability. Because the original visualization functioned primarily as an
				attention-grabbing article opener, it prioritized general trends over precise values. This redesign
				attempts to balance those competing goals while remaining aligned with the original visualization’s
				intended purpose.
			</p>
		</section>
	</main>
</div>

<style>
    .A3_report {
        width: 110ch;
        position: relative;
        left: 50%;
        transform: translateX(-50%);
    }
</style>

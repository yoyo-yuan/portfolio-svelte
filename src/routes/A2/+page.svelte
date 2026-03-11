<svelte:head>
    <title>Vis & Society Assignment 2</title>
	<link rel="stylesheet" href="https://vis-society.github.io/assignments/report.css" />
</svelte:head>

<div class="A2_report">
    <header>
        <h1>
            <small>Assignment 2</small>
            Exploratory Data Analysis
        </h1>

        <p>
            <strong>Yoyo Yuan</strong> — <em>yyyuan@mit.edu</em>
        </p>
    </header>
    <main>
        <section>
            <h2>Subtheme: Speculation</h2>

            <h3>Overall Analysis Questions</h3>
            <ol>
                <li>What is the relationship between the rate of owner-occupied properties and the rate of corporate-owned properties?</li>
                <li>What is the geographical distribution pattern of corporate-owned properties in Boston?</li>
                <li>Which Boston neighborhood has the most changes in the ownership patterns over time?</li>
                <li>What factors contribute most to large variations in the rate of corporate-owned housing?</li>
            </ol>
        </section>

        <section>
            <h2>Discoveries & Insights</h2>

            <figure>
                <img src="images/A2/Avg Own Occ Rate vs. Avg Corp Own Rate.png" alt="Average Ownership-Occupied Rate vs. Average Corporate-Owned Rate over 2004-2024" />
                <figcaption>
                <p>
                    I first plotted the average owner-occupied rate against the average corporate-owned rate
                    for the period 2004 to 2024 to perform a “gut check” on the data quality. I chose a
                    scatterplot because it allows readers to examine the precise data points directly, without
                    the additional visual structure imposed by connecting lines or shapes. I also used averages
                    of data to ensure that each neighborhood is weighted equally and not influenced by
                    differences in the number of observations. As expected, the two rates exhibit a strong
                    inverse relationship, roughly following a linear pattern with a slope close to -1. This
                    makes intuitive sense, since a corporate-owned property is typically not owner-occupied,
                    and vice versa.
                </p>
                <p>
                    Two neighborhoods, Downtown and South Boston Waterfront, appear farther to the right of
                    the general trend, indicating higher-than-average corporate-owned rates. These outliers
                    suggest areas that may require closer examination in relation to our broader analysis
                    questions. Fenway also stands out, as its owner-occupied and corporate-owned rates are
                    nearly equal. These observations raise a question: have the ownership patterns of these
                    neighborhoods fluctuated significantly over time?
                </p>
                </figcaption>
            </figure>

            <figure>
                <img src="images/A2/Average Rates over 2004-2024.png" alt="Average Rates Over 2004-2024: Corporate-Owned vs. Owner-Occupied Properties" />
                <figcaption>
                    In the background reading <i>When Private Equity Becomes Your Landlord</i>, the entry of Greystar
                    in 2017 prompted me to think more carefully about the timing and spread of property management
                    and investment firms in Boston. This contextual reference motivated me to pay closer attention
                    to temporal shifts in ownership patterns by plotting the corporate-owned and owner-occupied
                    property rates against time. The line graph illustrates the overall trend in those rates from
                    2004 to 2024, as indicated in the metadata file. I chose to plot the average rates across all
                    Boston neighborhoods because the mean provides a general overview without allowing individual
                    neighborhoods to disproportionately influence the interpretation. Using the sum would be
                    misleading, since the total across neighborhoods would exceed 1, which is not meaningful for
                    a rate. The average owner-occupied rate shows a slight downward trend but remains relatively
                    stable over the twenty-year period. In contrast, the average corporate-owned rate increases
                    dramatically, reaching approximately five times its level in 2004 with the most significant
                    jump occurring between 2019 and 2021. These vastly different trends prompted me to plot the
                    sum of the two average rates. Unsurprisingly, this combined rate resembles the growth pattern
                    of corporate-owned properties. However, it is notable that the total average rate ranges only
                    between 0.49 and 0.64, rather than approaching 1. This observation raises two immediate
                    follow-up questions: (1) Who owns the remaining share of properties in Boston? (2) How do
                    these rates vary across different neighborhoods?
                </figcaption>
            </figure>

            <figure>
                <img src="images/A2/Average Rates w: Residual over 2004-2024.png" alt="Average Rates Over 2004-2024: Corporate-Owned vs. Owner-Occupied vs. Other Properties" />
                <figcaption>
                <p>
                    To address the first follow-up question and the first analysis question, I created a new
                    variable by subtracting the average corporate-owned and owner-occupied rates from 1. This
                    allows readers to directly visualize the remaining “gray area,” representing properties
                    that are neither corporate-owned nor owner-occupied. I chose a stacked bar chart to
                    highlight the shift in distribution among the three categories, since their sum is always
                    1. Placing the “other” category at the bottom also makes it easier to observe whether it
                    increases or decreases over time. I continued using average aggregate values so that the
                    proportions remain interpretable and sum to 1.
                </p>
                <p>
                    The visualization shows that the “other” category remained relatively stable at around
                    0.5 until 2019, after which it began to decline steadily. To better understand what this
                    category represents, I examined the Boston Property Assessment dataset directly. I found
                    that many properties classified as neither owner-occupied nor corporate-owned belong to
                    absentee owners, individuals who own properties but do not live in those units. For
                    example, a person may own five properties but live in only one, leaving the remaining
                    four in this category.
                </p>
                <p>
                    It is plausible that many absentee owners are motivated by investment opportunities,
                    which connects to our subtheme of speculation. As a result, focusing solely on
                    corporate-owned properties may not fully capture the broader negative effects associated
                    with speculative ownership. I also observed that some owner-occupied properties contain
                    corporate-related keywords in the owner names. In these cases, the corporate designation
                    may function as a layer of anonymity to shield the owner’s identity in public records
                    rather than signaling an investment strategy. Because it is difficult to determine
                    individual ownership intentions or to reliably distinguish investment LLCs from other
                    ownership structures, it is reasonable to focus primarily on corporate-owned properties
                    for this analysis. Nevertheless, we should remain mindful of the dataset’s limitations
                    when interpreting these visualizations.
                </p>
                </figcaption>
            </figure>

            <figure>
                <img src="images/A2/Corp Own Rate by Space 2004.png" alt="Summary of Average Corporate-Owned Rate by Space in 2004" />
                <figcaption>
                <p>
                    To address the second follow-up question and my second analysis question, I used the
                    provided zip code data to create a map of Boston neighborhoods color-coded by their
                    corporate-owned property rates. I was particularly interested in exploring the geographic
                    distribution because I have limited familiarity with areas of Boston beyond downtown, and
                    a map allows for a clearer understanding of spatial relationships and concentrations.
                </p>
                <p>
                    To construct the visualization, I joined the Boston Neighborhoods Zipcodes dataset with
                    the Corporate Ownership and Occupancy Over Time dataset using the neighborhood field. I
                    then plotted the ZIP codes associated with each neighborhood, using darker shades to
                    represent higher corporate-owned rates. The data were filtered to display a specific year
                    for clearer comparison.
                    The resulting map shows that higher corporate-owned rates are concentrated in downtown
                    and Beacon Hill, while neighborhoods farther from the city center tend to have lower
                    rates. This spatial pattern aligns with my expectation, as centrally located and high-demand
                    areas are often more attractive to corporate or investment ownership.
                </p>
                </figcaption>
            </figure>

            <figure>
                <img src="images/A2/Corp Own Rate by Space 2024.png" alt="Summary of Average Corporate-Owned Rate by Space in 2024" />
                <figcaption>
                <p>
                    The overall spatial pattern in 2024 remains similar to that of 2004. High corporate-owned
                    rates are still concentrated around the downtown area. However, the northeastern region of
                    Boston saw a notable increase, with the South Boston Waterfront surpassing downtown to become
                    the neighborhood with the highest corporate-owned rate. One possible explanation is that
                    waterfront areas have attracted substantial development and investment over this period.
                    Increased construction and commercial expansion may have made these neighborhoods particularly
                    appealing to corporate buyers.
                </p>
                <p>
                    Although the relative color distribution across most neighborhoods resembles the 2004 pattern,
                    the overall scale has shifted upward. In other words, while the geographic ranking of
                    neighborhoods remains broadly consistent, corporate-owned rates have increased across Boston
                    as a whole.
                </p>
                </figcaption>
            </figure>

            <figure>
                <img src="images/A2/Own Occ Rate by Space 2004.png" alt="Summary of Average Owner-Occupied Rate by Space in 2004" />
                <figcaption>
                <p>
                    I then shifted my attention to the geographic distribution of the average owner-occupied rate
                    across Boston. As expected, the color scale for this map is roughly the inverse of the 2004
                    corporate-owned rate map. Neighborhoods such as West Roxbury, Roslindale, and Hyde Park, which
                    are farther inland, show higher owner-occupied rates. Housing prices in these areas are
                    relatively more affordable, making properties more accessible to individual buyers. At the same
                    time, corporations might expect fewer short-term appreciation opportunities in these neighborhoods,
                    directing their attention elsewhere. In contrast, downtown neighborhoods tend to have lower
                    owner-occupied rates. Property prices in these areas are often beyond the reach of many individual
                    residents, creating opportunities for corporations with substantial capital reserves to invest.
                </p>
                <p>
                    One notable difference is the South Boston Waterfront neighborhood in 2004. Although its
                    corporate-owned rate was only moderate at the time, its owner-occupied rate was exceptionally low.
                    This suggests a high concentration of absentee owners rather than corporate investors. One possible
                    explanation is that individual investors responded quickly to major infrastructure projects, such as
                    the completion of the Big Dig in 2004, anticipating future appreciation before large corporations
                    became heavily involved.
                </p>
                </figcaption>
            </figure>

            <figure>
                <img src="images/A2/Own Occ Rate by Space 2024.png" alt="Summary of Average Owner-Occupied Rate by Space in 2024" />
                <figcaption>
                <p>
                    Consistent with the earlier line graph, the overall average owner-occupied rate decreased slightly
                    from 2004 to 2024. Inland neighborhoods such as West Roxbury, Roslindale, and Hyde Park remain
                    dominated by owner-occupied properties, suggesting that investor interest has not grown substantially
                    in those areas. In contrast, Downtown and Longwood experienced declines in owner-occupied rates,
                    likely reflecting the construction of new luxury developments that attracted corporate buyers and
                    increased housing prices beyond the reach of many original residents. Interestingly, neighborhoods
                    such as South Boston Waterfront, Roxbury, and Beacon Hill saw increases in owner-occupied rates.
                    These unexpected patterns prompted a follow-up question: how has ownership rates shifted within
                    individual neighborhoods over time?
                </p>
                <p>
                    While the map visualizations effectively highlight geographic concentrations, they make it difficult
                    to compare changes across years since each map provides only a snapshot of a single year. Additionally,
                    when analyzing specific neighborhoods, I noticed two blank areas in the center of the Boston map.
                    Upon examining the zip code dataset more closely, I discovered that the neighborhood-to-zip-code
                    table is missing information for North End, West End, and Fenway. As a result, these neighborhoods
                    do not appear in the map visualization, despite having available data on corporate-owned and
                    owner-occupied rates. Their omission could lead to incomplete conclusions and the loss of potentially
                    important insights. Therefore, although the map provides useful spatial context, a traditional line
                    graph displaying neighborhood-level trends over time would more accurately and comprehensively
                    represent the dataset.
                </p>
                </figcaption>
            </figure>

            <figure>
                <img src="images/A2/Avg Own Occ Rate by Neighborhood.png" alt="Average Ownership-Occupied Rate by Neighborhood over 2004-2024" />
                <figcaption>
                    To conduct a more thorough analysis of all neighborhoods and answer my third analysis question, I
                    plotted a line graph of the average owner-occupied rate from 2004 to 2024, with separate lines for
                    each neighborhood. I chose to display this separately from the corporate-owned rate to improve
                    readability and make it easier to analyze shifts over time, especially in areas where multiple
                    lines intersect. Overall, most neighborhoods exhibit relatively stable or slightly declining trends over the twenty-year
                    period. While some neighborhoods, such as Chinatown, show minor year-to-year fluctuations, their overall
                    trajectories remain fairly consistent. In contrast, South Boston Waterfront stands out clearly, as its
                    owner-occupied rate displays substantial volatility between 2007 and 2020 and ultimately ends with a
                    slight net increase over the entire twenty-year period.
                </figcaption>
            </figure>

            <figure>
                <img src="images/A2/Avg Corp Own Rate by Neighborhood.png" alt="Average Corporate-Owned Rate by Neighborhood over 2004-2024" />
                <figcaption>
                    The line graph of average corporate-owned rates by neighborhood shows a steady upward trend overall,
                    consistent with earlier findings, though with noticeably greater year-to-year fluctuations. Complement
                    to the owner-occupied trends, Chinatown initially experiences a slight decline before joining the
                    broader upward trajectory observed across most neighborhoods. Once again, South Boston Waterfront
                    stands out with an irregular pattern. It exhibits particularly sharp increases in 2007, 2010, and the
                    period from 2020 to 2022. Although these fluctuations may seem unusual at first glance, they are
                    consistent with earlier visualizations in which this neighborhood repeatedly diverged from broader
                    citywide trends. This recurring pattern suggests that South Boston Waterfront needs more focused and
                    specialized analysis in future research.
                </figcaption>
            </figure>

            <figure>
                <img src="images/A2/Avg Corp Own Rate vs. Race Distribution.png" alt="Average Corp Own Rate vs. Race Distribution by Neighborhood over 2004-2024" />
                <figcaption>
                <p>
                    To address the fourth analysis question, I incorporated the provided U.S. Census data, which includes
                    demographic information on racial composition and age distribution by neighborhood. The Home for Profit
                    report on speculation in Greater Boston suggests that investor activity is often concentrated in
                    communities of color, which motivated me to explore potential relationships between race and corporate
                    ownership. I focused on the population aged 18 and over, as this group most closely represents
                    individuals who are likely to participate in the housing market as buyers or investors.
                </p>
                <p>
                    Despite the previously noted gaps in the zip code mapping data, I again used a geographic visualization.
                    This time, I overlaid pie charts representing the racial distribution of the 18-plus population in each
                    neighborhood on top of the map of corporate-owned rates. I believed that aligning demographic
                    distributions with geographic patterns of corporate ownership could provide useful preliminary insights.
                    While the Census dataset only provides data for 2020, I assumed that it serves as a reasonable
                    approximation of demographic averages across the 2004 to 2024 period. Given these limitations, this
                    analysis is intended to offer a broad overview rather than a definitive neighborhood-level conclusion.
                </p>
                <p>
                    From the visualization, white-majority neighborhoods appear to be concentrated in the northern areas of
                    Boston. At first glance, this suggested a possible positive correlation between corporate-owned rates
                    and the percentage of white residents aged 18 and above. However, closer inspection complicates this
                    interpretation. For example, West Roxbury and Jamaica Plain have relatively high percentages of white
                    residents but comparatively low corporate-owned rates. In contrast, Dorchester has a lower percentage
                    of white residents but a somewhat higher corporate-owned rate. These mixed patterns prompted me to
                    examine the owner-occupied rate visualization to determine whether complementary trends emerge.
                </p>
                </figcaption>
            </figure>

            <figure>
                <img src="images/A2/Avg Own Occ Rate vs. Race Distribution.png" alt="Average Own Occ Rate vs. Race Distribution by Neighborhood over 2004-2024" />
                <figcaption>
                <p>
                    The visualization comparing average owner-occupied rates with racial distribution by neighborhood
                    largely reinforces the patterns observed in the previous analysis. The northwest and central areas
                    of Boston tend to have higher percentages of white residents and lower average owner-occupied rates.
                    In contrast, several inland neighborhoods and some along the shoreline display lower percentages of
                    white residents alongside relatively higher owner-occupied rates. Again, there are notable exceptions
                    to these general patterns: West Roxbury, Roslindale, Jamaica Plain, South Boston, and Charlestown
                    have majority white populations but also relatively high owner-occupied rates; conversely, Roxbury
                    has a lower percentage of white residents and also a lower owner-occupied rate.
                </p>
                <p>
                    These mixed results suggest that racial composition alone is unlikely to be a dominant factor
                    driving fluctuations in ownership patterns. Instead, other underlying variables, such as income
                    levels, housing prices, or neighborhood developments, may play a more significant role and may
                    need further investigation.
                </p>
                </figcaption>
            </figure>
        </section>

        <section>
            <h2>Summary</h2>

            <p>
                In this exploratory data analysis, I examined the temporal and geographic patterns of corporate-owned
                and owner-occupied property rates in Boston from 2004 to 2024. I began by evaluating the data’s scope
                and limitations and found that: (1) the two rates are negatively correlated as expected; (2) the dataset
                spans the full 2004 to 2024 period; (3) ownership classifications may not be perfectly accurate due to
                challenges in distinguishing between corporate-owned and owner-occupied properties, so the data should
                be interpreted as providing a general overview rather than precise measurements; (4) the zip code
                dataset omits several neighborhoods, limiting the completeness of the map visualizations; and (5) the
                U.S. Census data only covers 2020, requiring the assumption that it reasonably approximates demographic
                patterns over the twenty-year period.
            </p>
            <p>
                I then used a range of visualizations to explore relationships between variables. Over time, the
                owner-occupied rate shows a slight decline, while the corporate-owned rate increases sharply,
                particularly after 2019. Spatially, corporate-owned properties are most concentrated in central
                and downtown areas, whereas owner-occupied properties are more prevalent in inland and some shoreline
                neighborhoods. However, South Boston Waterfront consistently exhibits irregular patterns across multiple
                visualizations, suggesting that it needs a more targeted analysis. Finally, I examined whether racial
                composition correlates strongly with ownership patterns. While some preliminary patterns emerged, the
                overall evidence suggests that race distribution alone is not a dominant factor driving changes in
                ownership patterns. Future research could therefore focus more closely on South Boston Waterfront and
                investigate additional underlying variables to better understand the forces shaping these trends.
            </p>
        </section>
    </main>
</div>

<style>
    .A2_report {
        width: 110ch;
        position: relative;
        left: 50%;
        transform: translateX(-50%);
    }
</style>

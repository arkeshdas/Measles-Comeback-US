# Final Writeup

**Arkesh Das**
**Project:** *Measles Comeback: Vaccination Gaps and Outbreak Risk in the United States*

## Project summary

For my final project, I used public datasets on measles cases, vaccination coverage, exemption rates, births, and population to study how measles has re-emerged in the United States and how that pattern relates to vaccination gaps. I combined national case data from the CDC, international case data from the WHO, U.S. vaccination coverage data from CDC ChildVax, state-level measles case data from the CDC and NNDSS, state-level kindergarten exemption data, U.S. births data, and Census population estimates. Because there were so many fragmented datasets I had to pull from, I reshaped and merged these datasets in Python inside my visualization scripts instead of making one master data file.

**The main questions I asked were:**

- How has measles incidence changed over time in the United States compared with Europe and the world? Do states with higher exemption rates appear more likely to experience outbreaks?
- How many unvaccinated children may be accumulating over time in the United States, even when vaccination percentages look relatively high?

Across the project, I was trying to make the argument that measles is not just “back” in a vague sense, but that its return is related to uneven vaccination coverage and policy choices, especially where exemption rates are higher or requirements are weaker.


**Final "Action Item"**

My final argument was that where vaccination requirements are weaker, outbreak risk is higher, and that this relationship becomes clearer when the data is structured to emphasize interpretable risk rather than raw counts or noisy correlations. I do not think my project proves a simple one-variable causal story, but it does show a meaningful and interpretable relationship between exemption rates and the probability of state-year outbreaks. It also shows that national vaccination coverage can look fairly stable while still leaving a large number of unvaccinated children over time, which helps explain why outbreaks can still occur.

## What I did

I built four main final visuals. The first compared measles incidence over time in the United States, the WHO European Region, and the world using cases per 100,000 people instead of raw case counts. The second showed the probability of a state-level outbreak across bins of kindergarten MMR exemption rates. The third paired annual MMR coverage with an estimate of cumulative unvaccinated children in the United States. The fourth was a series of choropleth maps showing state-level measles incidence over time.

A major part of the project was data cleaning and alignment. I had to combine multiple state case sources because the format and source changed across years. I also had to exclude non-state rows, reconcile naming inconsistencies like New York City versus New York, and restrict some parts of the analysis to years where the datasets meaningfully overlapped. These decisions reflect Cairo’s emphasis on prioritizing accuracy and clarity before aesthetics, as well as Tufte’s argument that data integrity depends on careful curation rather than simply plotting raw data.

I also made several deliberate design choices that were shaped by ideas from the course. I normalized cases by population so that large states would not dominate comparisons just because they have more people, which aligns with Tufte’s emphasis on truthful representation and Cairo’s argument that context is necessary for meaningful interpretation. At the same time, I intentionally used absolute counts when estimating unvaccinated children to preserve the real-world scale of the problem, reflecting the idea that representations should match the specific question being asked.

I structured the visuals as a sequence of evidence rather than independent charts, moving from global and national trends, to explanatory mechanisms like vaccination coverage and exemptions, and then to spatial patterns at the state level. This reflects ideas from Segel and Heer on narrative visualization, where layout and ordering guide the viewer through an argument. I also used international comparisons between the United States, Europe, and the world to provide context and avoid implying that rising measles cases are a universal trend, which aligns with Cairo’s emphasis on framing and with *Data Feminism’s* argument that context shapes interpretation.

For the exemption analysis, I intentionally moved away from a basic scatter plot and instead created a binned probability chart. A scatter plot preserved all observations but obscured the overall pattern due to noise and overplotting. By binning exemption rates and defining an explicit outbreak threshold, I transformed the data into a probabilistic relationship that is easier to interpret. This reflects findings from Cleveland and McGill on graphical perception, which show that humans interpret position and length more effectively than dense point clouds, as well as Tufte’s principle of simplifying without distorting. I added sample sizes to each bin to make the level of support visible, connecting to both Tufte’s emphasis on showing the data and *Data Feminism’s* focus on transparency.

I also made intentional visual design choices. I used restrained styling, consistent fonts, and a structured color scheme to reduce cognitive load and maintain focus on the data, reflecting Tufte’s concept of minimizing non-data ink. At the same time, I did not strictly adhere to minimalism when it conflicted with communication. Instead, I followed Cairo’s idea that visualizations should be both functional and engaging, using layout and visual hierarchy to guide attention and reinforce the central message. Overall, these decisions reflect the broader course theme that visualization design involves balancing tradeoffs rather than following rigid rules.

More generally, I simplified the data where it improved interpretability, while trying to avoid misleading transformations. This included discretizing exemption rates, defining categorical outcomes, and maintaining consistent encodings across visuals. These decisions reflect the idea, discussed throughout the course, that visualization is not just about displaying data but about helping viewers perceive meaningful structure.

## What I learned

The biggest thing I learned is that making a good visualization is not just about choosing a chart type. It is about deciding what comparison is fair, what level of aggregation is appropriate, what assumptions need to be made visible, and what kind of guidance the reader needs. This connected strongly to ideas from Tufte, Cairo, and *Data Feminism*.

From Tufte, I kept thinking about data integrity, data-ink, and the idea that design choices should be deliberate and justifiable. From Cairo, particularly Chapters 1 to 3, I took the idea that visualizations should be truthful, functional, insightful, and designed for communication rather than decoration. From *Data Feminism*, I took seriously the idea that data is not neutral and that choices about framing, context, and annotation shape how people interpret results. In my project, that meant not assuming the data would simply “speak for itself,” but instead making intentional decisions about what to highlight and how to present it.

The course also changed how I think about design tradeoffs. Earlier in the semester, I might have assumed that showing more raw data was always better. By the end, I had a better appreciation for the balance between completeness and interpretability. The exemption chart is a clear example. A scatter plot preserved all individual observations but obscured the overall pattern, while binning and aggregating the data made the relationship much clearer. This reflects course discussions about perception, as well as Cairo’s emphasis on clarity and Tufte’s idea that simplification is acceptable when it reveals structure rather than hiding it.

Another important takeaway for me was the role of narrative and audience in visualization design. Rather than treating visuals as neutral outputs, I made intentional decisions to guide the reader toward specific interpretations through layout, ordering, and annotation. This reflects ideas from Segel and Heer on narrative visualization, as well as broader course discussions about the tension between showing and telling. I leaned toward guided interpretation, which aligns with *Data Feminism’s* argument that visualization should help readers understand why a pattern matters, not just present the data.

## What went as expected, and what did not

What went as expected was that public health data could tell a strong story once it was cleaned and aligned. Once I got the datasets into compatible forms, the broad patterns were meaningful and visually compelling. I also expected that normalization would matter, and it did. Using cases per 100,000 made the comparisons much more defensible.

What did not go as expected was how much of the project would depend on data wrangling decisions rather than plotting code. Finding state-level measles data across a longer time span was harder than I expected, and some datasets that looked similar at first were not actually comparable without careful filtering. Vaccination coverage data was also messier than I expected because different sources used different age groups and reporting structures. These challenges reinforced course themes about how preprocessing decisions shape the final visualization and influence the conclusions that can be drawn.

I also found that some technically valid visualizations were not effective communication tools. Early scatter-based approaches did not clearly convey the relationship I was interested in, which forced me to rethink the design rather than forcing the data into a familiar chart type. This reflects the course emphasis that there is no single “best” visualization, only designs that are more or less effective for a given question and audience.

Overall, this project taught me that strong visualization work is not separate from data cleaning, statistical judgment, or ethical communication. Those things are all part of the same process. The final result is not just a set of charts about measles, but an argument about how careful design choices, including normalization, aggregation, and narrative structure, can turn fragmented public data into a clearer and more policy-relevant story.

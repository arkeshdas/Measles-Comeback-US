# Day 20 In class feedback


## Constructive Criticism:

Dan: Why is the world chart so much higher than the US? A bit confusing with US map showing there being measles cases but in other chart the US stays at 0.0. Definitely adjust axes. 
Maybe start with older map where cases are lower, then do the vax rates changes and then map at the end with higher cases. 

Madeline: The first map should be your first visualization because it really caught my eye. You should also see what’s going on in the random yellow spots outside of Texas. I like the scatter plots, but maybe there is a more creative way of showcasing the data. Also make sure you keep colorblindness in mind! You could use a gradient of the same color rather than completely different colors.

Allison: I would probably describe what MMR is in one of the plots or in the background of your poster/dashboard. In the first plot, I would recommend adding the exact years in the title like (1960-2023) because otherwise it may be hard to find the last year of the data. In the map, I would recommend making the title of the colorbar be ‘Number of Cases’ or “Case Count” to be slightly more clear. Maybe for the third plot you could add some kind of correlation computation to better compare how unvaccinated children compared to the vaccination rate. Wouldn’t it be a perfect negative correlation because a decrease in the estimated number of unvaccinated children would indicate an increase in the vaccination rate?

Araynah:
I would suggest adding some kind of  formal measures at the highest peaks of the graph maybe suggesting what could have caused certain spikes at certain years. Also expanding on what each abbreviation means. 

## How I will integrate this feedback

- For Figure 1: I am going to have to adjust the data from raw case numbers to percentage by population. 
- For Figure 2: I need to either find a combined dataset, or just plot one of the vaccination rate datasets. Ideally, I would have the same age for the entire dataset. The axises also need to be adjusted so that its 0 to 100 not an arbitrary number. Figure 2 might actually be kind of redundant, and I think to add an additional layer to this narrative, I should compare inscedence rates with another factor such as death or maybe some other landmark symptom so that I can see if we are getting better at treating measles or worse. I also need to explain what MMR is and stuff.
- For Figure 3: I think that this is the strongest figure, if I can tell the story properly. I think that to do that I will need to calculate the cumulative nubmer of unvaccinated kids. I also need to mess with the axis scales to show that vaccination rates are constant-ish, but small deviations in percantage coorespond to large shifts in raw number of unvaccinated kids. I should also look into annotating certain peaks, such as when COVID happened, etc and anything else that might be significant in the narrative.
- For Figure 4: I think that I should make this plot interactive or somehow show multiple years. 
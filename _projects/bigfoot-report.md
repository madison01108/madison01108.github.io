---
name: Bigfoot Sightings Reports
permalink: /projects/bigfoot-report/
tools: [Python, Altair, vega-lite]
description: Two Altair visualizations of Bigfoot sighting reports with an interactive season dropdown (HW 5).
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---
# Introduction

This page features two visualizations created in HW #5, where we used the Bigfoot Field Researchers Organization (BFRO) sightings dataset. I first used the pandas library to assist me with the data cleaning, filtering, and aggregration to ensure that my data was modified from the dataset to be called by the altair library properly. The altair library did most of the work with actually producing the visualizations, customized to the intentional design and interaction goals. These results were then exported with JSON for this page.

# 1. Bigfoot Reports by Season

<vegachart schema-url="{{ site.baseurl }}/assets/json/chart1.json" style="width: 100%"></vegachart>

I created a bar chart visualization with altair that depicts the count of total reports of Bigfoot by each season. Note that not a small minority of observations have been omitted as they had a value of 'Unknown' in the 'Season' column, which was problematic for our visualization. The 'Season' column was encoded as a nominal variable on the x-axis, while the total number of reports is a quantitative variable on the y-axis, which was produced from altair's `count()` encoding shorthand aggregate method. I also colored the bars by season using the altair's `category10` color scheme, as the original altair documentation page directs you to a list of color schemes, where 'category10' is ideal for encoding discrete data values as our season value function as distinct, nominal cateogories. I also renamed the original 'season' column from our dataset to`Season` to ensure that the title casing would be more cohesive with the rest of our visualization structure, since the other labels all have a consistent uppercase. I chose the 'Seasons' column as what we wanted to encode by here because it can reveal seasonal trends of Bigfoot reports by letting viewers understand which season(s) reports are clustered. In our visualization results, we can deduce that sightings cluster most in warmer months (specifically summer) when more people are likely to be outdoors. 
# 2. Yearly Distribution of Bigfoot reports by Season

<vegachart schema-url="{{ site.baseurl }}/assets/json/chart2.json" style="width: 100%"></vegachart>

For my second visualization, I developed a stacked bar chart that shows how reports change over a period of years. The 'Year' column was extracted from our original 'date' column, which means it is related to time but we want to encode it as an ordinal variable on the x-axis to show the change in total reports by the natural order of time values. Furthermore, native support for temporal encodings for data that only contains year values require much more work than ordinal encoding. This allows us to observe sequential changes in time by the x-axis. The number of total reports is again quantitative on the y-axis, and season is nominal and colored with the same `category10` scheme as the first chart so the colors will remaine consistent between the two plots.

# Interactivity
For the interactivity portion, I decided to implement an interactive dropdown menu for selecting a specific season within my second visualization, where selecting one season at a time highlights only the count of reports for a year by that specific season. This is a more user-friendly analysis method for allowing peoople to interpret a stacked bar in a more accessible manner by comparing yearly distributions of total reports by a specific season. Furthermore, the axes are fixed so the chart doesn't rescale in size each time someone selects a different season to filter by. This allows someone to understand whether the yearly period has an impact on seasonal patterns in Bigfoot sightings or if our seasonal trends can simply be generalized to multiple years.

<div class="left">
{% include elements/button.html link="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/bfro_reports_fall2022.csv" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/madison01108/madison01108.github.io/blob/main/python_notebooks/Workbook.ipynb" text="The Analysis" %}
</div>

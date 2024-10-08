---
layout: project
type: project
image: img/CITRUS/Influenza.jpg
title: "Detecting Patterns and Trends of Influenza A in the USA"
date: 2024-07-26
published: true
labels:
  - Data Science
  - Data Visualization
  - Python
summary: "In the summer of 2024, I was a part of the CITRUS Summer 2024 program which allowed me to develop my data science skills while researching a topic I was interested on."
---

<div class="text-center p-4">
  <img width="400px" src="../img/CITRUS/Presentation-Slide.jpg" class="img-thumbnail" >
  <img width="400px" src="../img/CITRUS/avg-case-week.png" class="img-thumbnail" >
</div>

My project, Detecting Patterns and Trends of Influenza A in the USA, was developed under the mentorship of the CyberInfrastructure TRaining for Undergraduates in Summer (CITRUS) program at the University of Hawaii. CITRUS is a research opportunity in a REU-style immersion to develop skills in CyberInfrastructure with a climate-based research project. The program entailed learning and developing data science skills which would then be applied as each mentee carried out their own research project surrounding a topic and data set of their choosing.

My topic focused on the intermingling of health and climate which led me towards wanting to apply data science techniques to identify patterns and trends of Influenza A in the USA. The research question I based my findings around was, “Are there any consistent patterns in the timing and intensity of influenza A seasons?”. I was able to find a dataset from the World Health Organization which had data on Influenza A cases in the USA from 1997 to 2024. I then cleaned the data, which included dropping columns and rows that were not relevant to this research question and filling in missing values. I then graphed my findings to provide a visual understanding of the data and applied various statistical tests (such as chi-squared and Kruskal-Wallis) to gain deeper insight to my question.

This project was completed by myself with the guidance of my graduate mentors that would be done through daily check-ins to see the progress of my research project. It gave me an opportunity to refine my data science coding skills and gave me an opportunity to apply research techniques. To be eligible to participate in this program I had to acquire a CITI conduct of research certificate that shows I understand the ethics behind researching. This program also let me develop my communication skills which were necessary when it came to sharing my findings through a final presentation conducted at the end of the program.

Here is a portion of my code that was used to plotted the graph above:
```cpp
# plot the average INF_A
  ax1.plot(merged_data['ISO_WEEK'], merged_data['INF_A'], marker='o', color='b', label='Average INF_A')
  ax1.set_xlabel('ISO WEEK')
  ax1.set_ylabel('Average INF_A Cases', color='b')
  ax1.tick_params(axis='y', labelcolor='b')

# create a second y-axis to plot the average SPEC_PROCESSED_NB
  ax2 = ax1.twinx()
  ax2.plot(merged_data['ISO_WEEK'], merged_data['SPEC_PROCESSED_NB'], marker='o', color='r', label='Average SPEC_PROCESSED_NB')
  ax2.set_ylabel('Average SPEC_PROCESSED_NB', color='r')
  ax2.tick_params(axis='y', labelcolor='r')
```
To see more of my code, you can click [here](https://github.com/shaelyn-l/CITRUS-2024.git) to go to the project repository.

For more information regarding this project, you can see my final presentation [here](https://docs.google.com/presentation/d/1tGAJVMcuSHLmi7Si2j87I2ENSzEC9S1xj7CoL6TqFCM/edit?usp=sharing).


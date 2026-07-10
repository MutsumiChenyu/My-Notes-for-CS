
Chenyu Wang 王辰宇--525370910188

## Overall Analysis


This project analyzes reported crime records in Chicago from 2014 to 2025. The full dataset is first cleaned and split so that recent years, especially 2024 and 2025, can be analyzed more efficiently. Community boundary data is also corrected before geographic visualization, because malformed boundary strings would affect map-based plots.

Overall, the figures suggest that Chicago crime reports are not evenly distributed across years, categories, locations, or time periods. The yearly trend shows a clear decrease around 2020-2021, followed by a recovery in 2022-2024 and a lower value in 2025. Crime type analysis indicates that theft-related crimes and battery are major components of the dataset. Spatial plots show that crimes are concentrated in some police districts and community areas instead of being evenly spread across the city. The time-pattern heatmap further shows that reported crimes are more common around midnight and in afternoon-to-evening periods, while early morning hours tend to have lower activity.

## Figure 1. Yearly Reported Crimes 
  


![[e5d9524e91dc32d434c829a629cc62f2.png]]
  

This bar chart shows the annual number of reported crimes in Chicago from 2014 to 2025. The counts were relatively high and stable before 2019, then dropped clearly in 2020 and 2021, which may be related to pandemic-period changes in city activity and reporting patterns. Crime reports increased again from 2022 to 2024, while 2025 is lower than the previous two years.

  

## Figure 2. Average Accumulated Monthly Crimes

  

![[94c5cd09f25fc1f6707c43134ef435de.png]]

  

This line plot shows the average accumulated number of crimes by month from 2014 to 2025. The curve increases almost steadily from January to December, meaning reported crimes accumulate at a fairly regular monthly pace. The final average yearly total is about 255,000 cases.

## Figure 3. Predicted and Actual Accumulated Crimes in 2025

![[Pasted image 20260711005702.png]]

The predicted accumulated crime count remains consistently higher than the actual count after April. By December, the model overestimates the annual total by approximately 14,000 cases. Therefore, the monthly growth pattern of 2024 captures the general increasing trend but does not accurately predict the lower crime level in 2025.

## Figure 4. Primary Crime Type Distribution

  

![[60a60d24ee59c7c9f6206eee546fe7f2.png]]

  

This pie chart compares the most frequent primary crime types from 2014 to 2025. `THEFT` is the largest category, followed by `BATTERY`, showing that property crime and violence-related reports are major parts of the dataset. The large `others` slice also shows that less frequent crime types still contribute a substantial combined share.

  

## Figure 5. Crime Description Word Cloud

  



![[2c3bd03186f5ee078791d26939b457d5.png]]  

This word cloud presents frequent secondary crime descriptions in 2025. Large phrases such as `SIMPLE`, `DOMESTIC BATTERY SIMPLE`, `RETAIL THEFT`, `TO VEHICLE`, `$500 AND UNDER`, and `OVER $500` indicate that simple battery, retail theft, vehicle-related crimes, and property-value-based theft descriptions are especially common.

  

## Figure 6. Crime Distribution by Police District

  


![[9d7b4abf7a15e1f0a7078128c0c6f8dc.png]]
  

This geobubble map shows 2025 crime counts by police district. Larger bubbles represent districts with more reported crimes. The map reveals that crime reports are spatially uneven, with some districts having around fifteen thousand cases while others have far fewer.

District  had the highest number of reported crimes, with  cases; while District YY had the lowest, with  cases.

  

## Figure 7. Crime Location Density with Community Area Boundaries

  
![[7902feadabef0603aaa5e3ecb4a1e2f0.png]]


  

This map combines crime density in 2025 with Chicago community area boundaries. Darker regions indicate stronger concentrations of reported crimes, and the boundary labels make it easier to connect dense regions with specific community areas. The pattern shows that crime concentration is not uniform across the city.

  

## Figure 8. (Self-selected) Crime Time Pattern in 2025

![[a27c36faaeae27b372b9b7e83e6e7bd9.png]]
  

This self-selected heatmap compares crime frequency by day of week and hour of day in 2025. The brightest areas appear around midnight and during afternoon-to-evening hours, while early morning hours around 4-6 are generally lower. This suggests that crime reports follow clear time patterns rather than occurring uniformly throughout the week.
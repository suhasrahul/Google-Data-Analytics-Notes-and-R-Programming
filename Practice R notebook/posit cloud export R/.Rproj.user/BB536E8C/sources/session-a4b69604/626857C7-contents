data("ToothGrowth")
View(ToothGrowth)
# Install filter function 
install.packages("dplyr")
library(dplyr)
# Now will filter by dose and arrage or sort by teeth lenght 

filtered_tg <- filter(ToothGrowth,dose==0.5)
View(filtered_tg)

arrange(filtered_tg,len)

# Using same filter with nested function we get same result as prevous 2 steps

arrange(filtered_tg, len)

# Using same filter with pipe function 

filtered_pipe <- ToothGrowth %>%
  filter(dose==0.5) %>%
  arrange(len)

# Data with bad values
data <- c(11, 7, NA, 9, NA, 13, 15, NaN, 19, 17, 14, NaN)

data <- ifelse(is.na(data)|is.nan(data), "missing",        
            ifelse(data < 10, "low",
                   ifelse(data < 15, "medium", "high")))

data
table(data)

# assignment8.R
# choose file interactively
student6 <- read.table(
  file.choose(),
  header = TRUE,
  sep = ",",
  stringsAsFactors = FALSE
)

head(student6)

library(plyr)

gender_mean <- ddply(
  student6,
  "Sex",
  summarise,
  GradeAverage = mean(Grade, na.rm = TRUE)
)

gender_mean

write.table(
  gender_mean,
  file = "gender_mean.txt",
  sep = "\t",
  row.names = FALSE
)

i_students <- subset(
  student6,
  grepl("i", Name, ignore.case = TRUE)
)

write.csv(
  i_students$Name,
  file = "i_students.csv",
  row.names = FALSE,
  quote = FALSE
)

write.csv(
  i_students,
  file = "i_students_full.csv",
  row.names = FALSE
)

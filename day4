install.packages(c("vegan", "DarkDiv"))

library(DarkDiv)
library(vegan)

dat <- read.csv("data/data_biomac_2.csv")
dim(dat)
dat[1:5, 1:10]

comm <- dat[, 6:ncol(dat)]

### DarkDiv package
?DarkDiv
dark_comm <- DarkDiv(comm, method = "RawBeals")
dark_comm_vegan <- vegan::beals(comm)
str(dark_comm)
str(dark_comm_vegan)

dark_comm$AllProbs[1:5, 1:5]
dark_comm_vegan[1:5, 1:5]

max(dark_comm$AllProbs)
min(dark_comm$AllProbs)
mean(dark_comm$AllProbs)
median(dark_comm$AllProbs)

# very few species have an high probability of occurrence
# because few species occur frequently, and many species 
# occur rarely

quantile(dark_comm$AllProbs) 

### Dark Diversity s.s. 10.1111/geb.13203
rowSums(dark_comm$Dark) # NAs (i.e. missing values) should be accounted for when summing or doing other operations
dd <- rowSums(dark_comm$Dark, na.rm = T) # "na.rm = T" argument enables us to sum values by removing NAs
dd # our dark diversity vector (1 value per site/plot -> 19 values)
hist(dd,
     main = "Histogram of probabilistic dark diversity")
summary(dd)

boxplot(dd[1:10], dd[11:19]) # here we graphically compare dark diversity values between the first ten plots and last 9 plots
boxplot(dd[dat$Management == "F"], dd[dat$Management == "C"]) # here we do the same based on management
t.test(dd[dat$Management == "F"], dd[dat$Management == "C"]) # here we use a test to check for differences between the two groups

### Community completeness -> ln(observed richness/dark diversity) (see 10.1007/s12224-013-9169-x)
sr <- specnumber(comm)
cc <- log(sr/dd)
cc
hist(cc)
summary(cc)

boxplot(cc[dat$Management == "F"], cc[dat$Management == "C"])
t.test(cc[dat$Management == "F"], cc[dat$Management == "C"])


### Range filling -> realized/potential range size 10.1111/j.1461-0248.2004.00614.x
sf <- specnumber(comm, MARGIN = 2) # species frequencies -> realized range size
pr <- colSums(dark_comm$Pool) # potential range 
rf <- sf/pr
rf
head(sort(rf, decreasing = T), 20)
head(sort(rf), 20)

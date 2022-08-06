### CALCULATOR
###########################
install.packages("indicspecies")

3 + 3

# assignment of a variable
somma <- 3 + 3

somma
# assign & print
(somma <- 5 + 6)

prodotto <- 2 * somma

# list of variables
calc <- list()
calc$somma
calc$a <- 5
calc$prodotto <- 2 * (3 + 3)

calc[1]
calc[1:3]
calc["somma"]
calc[c(1, 3)]
calc$somma

calc$somma[2] <- 7 + 23
calc$somma


calc$result <- calc$somma[1] + calc$somma[2]
calc

### COMMUNITY MATRIX: vegan::dune CO-OCCURENCE DATA
###########################
# 
library(vegan)
?vegan
# library(tidyverse)

data(dune)
data(dune.env)

# dimensions (rows, columns, cells)
# in R: data[row(s), column(s)]
dim(dune)
class(dune)
row.names(dune)
colnames(dune)
dune[5:7, 5:9]

head(dune)
tail(dune)
dune[3:5, 3:7] > 2
dune[1:5, 1:5] > 0

rowSums(dune[1:5, 1:5] > 0)

# species richness
rich <- rowSums(dune > 0)
rich
class(rich)

library(tidyverse)

ctrl + shift + M

# Using pipe-lines of tidyverse
a <- rich %>% 
  sort() %>% 
  as.data.frame() %>% 
  rename(richness = ".")

# Translate in R base
a <- sort(rich)
a <- as.data.frame(a)
colnames(a) <- "richness"
a

###
dim(rich)
class(rich)
length(rich)


table(rich)

?hist

hist(rich, 
     main = "Species richness",
     xlab = "number",
     ylab = "Frequency") 


### MULTIVARIATE ANALYSES: CLUSTERING AND ORDINATION
##########################

vegan::specnumber(dune) # built-in function of vegan library to calculate species richness

rowSums(dune) 
max(dune)

b <- dune %>% 
  rownames_to_column("id") %>% 
  pivot_longer(!id, names_to = "sp", values_to = "cover") %>% 
  filter(cover > 0) %>% 
  pull(cover) %>% 
  unique() %>% 
  sort()

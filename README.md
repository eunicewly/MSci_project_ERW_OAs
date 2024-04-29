# MSci_project_ERW_OAs

## Jupyter Notebook 
The data and codes for the MSci project - Elements released by terrestrial enhanced weathering of basanite due to reactions with organic acids can be found in the MSci_project_Eunice.ipynb in this repository.

The sample labels are as follow:

1: Citric control

2: Citric experiment

3: Citric (half) control

4: Citric (half) experiment

5: Maleic control

6: Maleic experiment

7: Oxalic control

8: Oxalic experiment

10: HCl control

11: HCl experiment

## PCA in R
PCA is performed in R. The codes used are:

For PCA with all acids
```
test5 <- read.csv('pca_test_all(pH_added_removed_Sr_Mo_ZEROS_added).csv', header=TRUE, row.names = 1)
# removing Na, S and Zn
test5 <- test5[, !(colnames(test5) == "Na")]
test5 <- test5[, !(colnames(test5) == "S")]
test5 <- test5[, !(colnames(test5) == "Zn")]
pc5 <- prcomp(test5,  scale. = TRUE) 
biplot(pc5) # creating biplot

#calculating variance, then proportion of total variance explained by each PC
pc5_var <- pc5$sdev^2
pc5_prop <- pc5_var/sum(pc5_var)*100
plot(pc5_prop,xlab='Principal Components',ylab='Propotion of variance (%)')
```

For PCA with only organic acids (OAs)
```
# PCA WITHOUT HCL, with only OAs
test6 <- read.csv('pca_test_all(pH_added_removed_Sr_Mo_ZEROS_added).csv', header=TRUE, row.names = 1)
hcl <- c("HClA","HClB","HClC","HClD","HClE","HClF","HClG")
test6 <- test6[!(rownames(test6) %in% hcl), ]
test6 <- test6[, !(colnames(test6) == "Na")]
test6 <- test6[, !(colnames(test6) == "Zn")]
pc6 <- prcomp(test6, scale. = TRUE,centre=TRUE)
biplot(pc6)

#calculating variance, then proportion of total variance explained by each PC
pc6_var <- pc6$sdev^2
pc6_prop <- pc6_var/sum(pc6_var)*100
plot(pc6_prop,xlab='Principal Components',
     ylab='Propotion of variance (%)')

```






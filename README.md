# Machine-Learning-DS675-MIMIC-Dataset-Project

Data -> missing values -> dropping or if in any column 50% missing drop column, if less than 10% missing in row - impute the values, label column has vital values, 

its not possible to do clustering so we did pivoting on the basis of patient id as there are multiple vitals of a single patien, there are 164 patients, 

made separate columns for patients via pivoting

cant drop missing values as its patient vitals so we imputed the missing values

label encoding for gender and admission types

k means we made cluster

imputation was so much that even making clustering was not segregating the clusters to some extent

pca - principal componetn analysis used that segregated the clusters to some good extent

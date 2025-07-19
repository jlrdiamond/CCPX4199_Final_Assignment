# CCPX4199_Final_Assignment
This repository contains a working R script, a comma separated values (CSV) file, and a READ.me file for analyzing lab-confirmed measles and rubella cases and annual population size by country for the years 2012 through 2024. The data for this comes from the World Health Organization (WHO) dataset in the rfordatascience/tidytuesday/data/2025/2025-06-24 Github repository path.

The aims of this analysis are to 1) compare the mean prevalence of annually-reported, lab-confirmed measles cases in all countries from 2012 through 2024 to those of rubella cases for the same time period by evaluating the hypothesis that there is a statistically significant difference between worldwide average number of lab-confirmed measles cases and average number of lab-confirmed rubella cases from 2012 through 2024, and 2) understand the relationship between annually-reported country population size and annually-reported, lab-confirmed measles and rubella cases in all countries for the same time period.

Aims:

This code meets that aim by 1) running a paired t-test to compare the average number of lab-confirmed measles cases for 2012 through 2024 for each country (avg_measles), average number of lab-confirmed rubella cases for the same time period for each country (avg_rubella),
and 2) calculating the Pearson correlation coefficient, r for the relation amongst the variables, annually-reported population size (annualized_population_most_recent_year_only), lab-confirmed measles (measles_lab_confirmed), and lab-confirmed rubella (rubella__lab_confirmed) for 2012 through 2024 for all countries, and 3) visualizing the linear relationships amongst the variables by plotting their averages.

Results: 

With a test statistic of 4.55 and a p-value of 9.0x10-6, we reject the null hypothesis and conclude that there is a statistically significant difference between worldwide average number of lab-confirmed measles cases and average number of lab-confirmed rubella cases from 2012 through 2024. On average, a country reports 350 more measles cases per year than rubella cases. These results indicate that there has been a higher global disease burden from lab-confirmed measles cases than from lab-confirmed rubella cases from 2012 through 2024.  

With an r value of 0.48, annually-reported population size and lab-confirmed measles cases share a positive, moderate linear relationship; with an r value of 0.33, annually-reported population size and lab-confirmed rubella cases share a positive, weak linear relationship; and with an r value of 0.10, lab-confirmed measles cases and lab-confirmed rubella cases share a positive, weak linear relationship. 

One limitation of this analysis was outliers. India and China are the only countries that reported annual population sizes over 1.0x109, an order of magnitude greater than the population sizes of other countries. To visualize the average annual measles cases and average annual rubella cases by average annual population size for 2012 through 2024, data for these two outlier countries were omitted.  

Dependencies or packages needed:

To run this code, importing the dplyr, readr, ggplot2, tidyr, purr, and broom packages, and installing and importing the Hmisc package is required. The dplyr package comprises operators and functions needed to manipulate data (Wickham et al., n.d.). The readr package allows for reading rectangular data from delimited files (Wickham et al., n.d.).  The ggplot2 package is required for creating data visualization graphics (Wickham et al., n.d.). The Hmisc package holds the rcorr() function needed to calculate Pearson correlation coefficient, r and an associated p-value (Harrell, 2025). It also requires loading the stringr package, which includes functions for manipulating strings (Wickham, n.d.).

Instructions on how to run the code: 

Use the following code script to load the necessary packages into the notebook: 

library(dplyr) #a "grammar" of data manipulation. ex: it includes the pipe operator, %>%. it expects tidy data (variables are columns, each row is an observation, values are the cells). provides verbs that help solve most common data manipulation challenges. includes: mutat(), select(), filter(), summarise(), arrange(). These work with group_by(). 
library(readr)  #package for reading rectangular data from delimited files like comma-separated values (CSV) and tab-separated values (TSV). See https://r4ds.hadley.nz/data-import for basics of use (https://readr.tidyverse.org/)
library(ggplot2)  #system for creating graphics (https://ggplot2.tidyverse.org/); could consider to be R analog to Matplotlib for Python
install.packages("Hmisc") #install Hmisc package, which contains rcorr() function
library(Hmisc)  #load the package
library(stringr)  #package that allows breaking lines of text of a given number of characters into lines of a smaller number of characters 

Using the following code in R, read the following World Health Organization (WHO) dataset directly from the rfordatascience/tidytuesday/data/2025/2025-06-24 public repository path in GitHub: 

cases_year=read.csv('https://raw.githubusercontent.com/rfordatascience/tidytuesday/main/data/2025/2025-06-24/cases_year.csv')

Alternatively, download the dataset as a .csv file, cases_year.csv and use the following code to load the file that into your notebook:

#Load downloaded .csv file
#cases_year <- read.csv('path/to/file')  #fill in with file path to where you saved the .csv file

Alternatively, download the dataset as a .csv file, cases_year.csv and use the following code to load the file that into your notebook:
cases_year <- read.csv('path/to/file')  #fill in with file path to where you saved the .csv file 
The code script is in the final_assignment_R_script file uploaded to this repository. 
Run the code blocks in the order in which they are listed. Each section has a note with general aim of that section, and each code line has a note with the aim of that line. 
The expected output for the rest of the steps in the script is below:
Step 2 should load the dataset from Github (see the alternative code to use above). 
Step 3 has two options: print(cases_year) allows viewing the entire dataset, while head(cases_year) allows viewing the first 6 rows of the dataset. Since there are 2382 rows in the dataset, viewing the first 6 to get a sense of the data in the notebook would be more wieldy.
Step 4 should create a new dataframe for ccases from 2012 through 2024 with any values of NA in the annualized_population_most_recent_year_only, measles_lab_confirmed, and rubella_lab_confirmed columns. 
Step 5 creates a new dataframe with calculated averages of the values of the three columns named in Step 4 in preparation for conducting a t-test. 
Step 6 yields results in a tibble from a paired t-test using averages of the columns names in Step 4.
Step 7 yields the results of the calculated the r values describing the linear relationships between the three variables named in Step 4.
Step 8 yields a scatterplot with line of best fit with the 2012 through 2024 average numbers of lab-confirmed measles cases by annual population. 

References:
Harrell, F. (2025, April 3). Rcorr: Matrix of correlations and p-values. rdrr.io. https://rdrr.io/cran/Hmisc/man/rcorr.html 
(2025, July 2). tidytuesday. Github. https://github.com/rfordatascience/tidytuesday/blob/main/data/2025/2025-06-24/readme.md#cases_yearcsv 
Wickham, H. (n.d.). stringr. tidyverse.org. Retrieved July 12, 2025. https://stringr.tidyverse.org/ 
Wickham, H., François, R., Henry, L., Müller, K., & Vaughan, D. dplyr. tidyverse.org. Retrieved July 12, 2025. https://dplyr.tidyverse.org/ 
Wickham, H., Chang, W., Henry, L., Pedersen, T. H., Takahashi, K., Wilke, C., Woo, K., Yutani, H., Dunnington, D., & van den Brand, T. ggplot2. tidyverse.org. Retrieved July 12, 2025. https://ggplot2.tidyverse.org/
Wickham, H., Hester, J., & Bryan, J. readr. tidyverse.org. Retrieved July 12, 2025. https://readr.tidyverse.org/ 
<img width="468" height="635" alt="image" src="https://github.com/user-attachments/assets/c7f7263e-b0e5-4fed-b35b-d4b67d9bdd7e" />

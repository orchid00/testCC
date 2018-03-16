# This a test and proof of concept
## By Paula Andrea Martinez

### Exposure to the coding club

Last updated on March 16th, 2018

#### Tutorial Aims:

1. Create a coding tutorial and host it on GitHub
2. Set up version control with GitHub and RStudio 
3. Analyse and visualise data using the tidyverse 
4. Create a reproducible report using R Markdown 

You can get all of the resources for this tutorial from [this GitHub repository](https://ourcodingclub.github.io/2018/03/06/tidyverse.html){:target="_blank"}. Clone and download the repo as a zip file, then unzip it.

### Lessons learned

## 1. Create a coding tutorial and host it on GitHub

I created this GitHub page and used the Architect theme. 

1. Create a GitHub repo
2. Create a markdown file called index.md (this is the index.md)
3. Go to your repo settings, scrowl down to GitHub Pages 
4. Change None for master branch for GitHub Pages
5. Optional: choose a theme
6. Refresh the page and go back to the section Github Pages. It will have your page link after "Your site is published at"

## 2. Set up version control with GitHub and RStudio 

Done this on my PC before hand.
I didn't know you can use # for comments on .gitignore :D
Most other things I knew, which I learned by doing and I definitely recommend Jenny Brian's tutorial Happy Git with R
[http://happygitwithr.com/](http://happygitwithr.com/), it is the best!

## 3. Analyse and visualise data using the tidyverse

Done parts 1, 2 and 3 from the reference [repo](https://ourcodingclub.github.io/2018/03/06/tidyverse.html){:target="_blank"}

Here is a summary of what what I've learned and some recommendations.

1. First, and most importantly, use a project. I will suggest an RStudio project. [It's good practice](https://www.tidyverse.org/articles/2017/12/workflow-vs-script/){:target="_blank"}.
2. This exercise requires a number of packages that you might not need for your analysis. Hence, I recommend using the R package `packrat` which will install packages only for your project. Read more about it [packrat](https://rstudio.github.io/packrat/){:target="_blank"}.
3. Make a folder sctructure, this is really important and also it's good practice. I have the following folders
  * packrat (for all packages installed)
  * fig (for all figures)
  * RData (this project uses RData, you might as well have a data folder for raw data)
  * scripts (where your R code lives)
  * You can have other folders too, but I consider those the basics.
4. Have a setup script to check and install all your packages 
5. We will be using a theme for the figures, I will have this in a separate script.
6. I followed the cleaning steps, and updated things slightly, as can be seen in my report (next step).
7. I think, it is good practice to always check how the data looks, hence I have a lot of dim and glimpse functions. That is optional.
8. From the tutorial we needed to install ggMargins again from the github repo, this because it seemed to have a change which was not showing our shaded area. Use this: devtools::install_github("daattali/ggExtra"). I've also learned that this is the preferred way to do it to have the latest changes of a package.
9. Oh, related to that, I've learned that if you need updates for R you have to install R the manual way (download and install), but there is an option in RStudio, help, Check for updates. It might update it for you or it might just let you know that you need to update.
10. A few **updated** pieces of code to look for
  * To clean names
  
        nams <-
        colnames(LPDdata_Feb2016)  %>%
        tolower %>%  # change caps for lower
        str_replace_all("[.]", "_")  # change dots for underscores

  * Clean data inside
  
        LPDdata_Feb2016_cleaned <- LPDdata_Feb2016 %>%
        mutate_all(~str_replace_all(., "/n", "")) %>%  # clean extra lines
        mutate_all(str_trim) %>%  # clean any extra spaces
        mutate_all(~str_replace_all(., "��", "-")) # arbitrary change for strange char
  
  * group_by
  I've learned that after summarise only the last grouped is drop. Unlike what I was thinking that all the groups are drop. You can read more about it [here](https://github.com/tidyverse/dplyr/issues/2963){:target="_blank"}
  * do
  I've learned recently that do is deprecated from [twitter Mike FC](https://twitter.com/coolbutuseless/status/969853912990720005), that is still an on going and fun discussion, but in trying to understand the options I found very nice tutorial of group_by + nest + mutate + map from Jenny Brian, highly recommended [Split-Apply-Combine](http://stat545.com/block024_group-nest-split-map.html){:target="_blank"}. My version of the forest_slopes can be found in the [report](https://orchid00.github.io/testCC/tidyverse_report.html){:target="_blank"}
  

## 4. Create a reproducible report using R Markdown 

Have a look at part one of the tutorial [https://orchid00.github.io/testCC/tidyverse_report.html](https://orchid00.github.io/testCC/tidyverse_report.html){:target="_blank"}

This is the end of the tutorial. 
Next, I will try to reproduce a map with some other things on it.
Happy R learning. 
Thanks Coding Club and Gergana Daskalova.


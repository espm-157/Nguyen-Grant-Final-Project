## Lab Summary

This project serves to answer three primary questions focuses on the topic of GHG emissions: Is the average greenhouse gas emissions from CAIT (China excuded) countries going down? Do individual greenhouse gasses follow the trend of GHG's as a whole and what is the percentage of each individual gas emission relative to all gas emissions? What are the GHG emissions relative to economic sectors and what is the breakdown for USA's emissions. 

The purpose of these observations is to elucidate if the rate of GHG emissions is going down and give information on what gases and sectors of the economy in countries like the US are most emission heavy. For the future, policy makers should work on decreasing GHG emissions for these sectors and most common greenhiuse gasses.


A description of the data required, and how it will be obtained (e.g. URL/DOI to data source): https://datasets.wri.org/dataset/cait-country 
  
  Data will be in csv format and contain metric tons of GHG emissions by country, gas, sectors, and subsectors from start of data collection 1990 till 2011.

3 questions / analysis tasks you will perform on the data; in the spirit of the assignments we have been doing:
  
  I will be importing my csv in r and I will use dyplr, ggplot, and more libraries to create new variables like total GHG emissions by country and average GHG rates, which includes use of custom R functions
  I will also be creating detailed visual representations of my findings in the form of bar charts and graphs. 
  Essentially I want to see which country is emitting most and their rate of emission.
  I want to also explore emissions by gas and sector of the economy in the US. 


![Reproducibility](https://github.com/espm-157/Nguyen-Grant-Final-Project/workflows/Reproducibility/badge.svg)

## Team Members:

- Grant Nguyen, grantnguyenq

This repository is a template for your team's repository.

## assignment

All work for this assignment should be in the `assignment` directory.  You will work in the `.Rmd` notebook, and commit your rendered output files (`.md` and associated files) in the `assignment` directory as well.

## Special files

All team repositories will also include most of the special files found here:

### Common files

- `README.md` this file, a general overview of the repository in markdown format.  
- `.gitignore` Optional file, ignore common file types we don't want to accidentally commit to GitHub. Most projects should use this. 
- `<REPO-NAME>.Rproj` Optional, an R-Project file created by RStudio for it's own configuration.  Some people prefer to `.gitignore` this file.


### Infrastructure for Testing

- `.travis.yml`: A configuration file for automatically running [continuous integration](https://travis-ci.com) checks to verify reproducibility of all `.Rmd` notebooks in the repo.  If all `.Rmd` notebooks can render successfully, the "Build Status" badge above will be green (`build success`), otherwise it will be red (`build failure`).  
- `DESCRIPTION` a metadata file for the repository, based on the R package standard. It's main purpose here is as a place to list any additional R packages/libraries needed for any of the `.Rmd` files to run.
- `tests/render_rmds.R` an R script that is run to execute the above described tests, rendering all `.Rmd` notebooks. 





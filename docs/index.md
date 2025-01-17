--- 
title: "Uniform Crime Reporting (UCR) Program Data: A Practitioner's Guide"
author: "Jacob Kaplan"
date: "2021-04-04"
site: bookdown::bookdown_site
documentclass: book
bibliography: [book.bib, packages.bib]
biblio-style: apalike
link-citations: yes
description: "This is a comprehensive guide to using the FBI's Uniform Crime (UCR) Reporting Program Data, a collection of crime and arrest datasets which are often referred to as 'UCR data.'"
graphics: yes
always_allow_html: yes 
colorlinks: yes
fontsize: 12pt
classoption: openany
---






# Preface 

If you've read an article about crime or arrests in the United States in the last half century, in most cases it was referring to the FBI's Uniform Crime Reporting Program Data, otherwise known as UCR data. UCR data is, with the exception of the more detailed data that only covers murders, a *monthly number of crimes or arrests reported to a single police agency* which is then gathered by the FBI into one file that includes all reporting agencies. Think of your home town. This data will tell you how many crimes were reported for a small number of crimes or how many people (broken down by age, sex, and race) were arrested for a (larger) set of crimes in that city (if the city has multiple police agencies, it will use the agency which is the primary agency on the case, usually the local police department) in a given month. This is a very broad measure of crime, and its uses in research - or understanding crime at all - is fairly limited. Yet is has become - and will likely remain among researchers for at least the next decade - the most important crime data in the United States.

UCR data is important for three reasons: 

1. The definitions are standardized and all agencies follow them so you can compare across agencies and over time.
2. The data is available since 1960 so there is a long period of available data.
3. The data is available for most of the 18,000 police agencies in the United States so you can compare across agencies.

For most of this book we'll be discussing the caveats of the above reasons - or, more directly, why these assumptions are wrong - but these are the reasons why the data is so influential. 

## Motivation

By the end of each chapter you should have a firm grasp on the dataset the covered and how to use it properly. However, this book can't possibly cover every potential use case for the data so make sure to carefully examine the data for your own particular use. This benefits you because you'll know your data better and become a better research because of it. This benefits me because it'll increase the quality of research in my field. 

I get a lot of emails from people asking questions about this data so part of my motivation for writing this book is to create a single place that answers as many questions as I can about the data. Again, the UCR data collection are the most commonly used crime datasets and there are still many current papers published with incorrect information about the data (including such simple aspects like what geographic unit data is in and what time unit it is in). So hopefully this book will decrease the number of misconceptions about this data, increasing overall research quality.^[Ideally, this will also decrease the number of emails and increase the number of citations I receive.]

## Structure of the book

This remainder of this book will be divided into eight chapters: an intro chapter briefly summarizing each dataset and going over overall issues with UCR data, seven chapters each covering one of the seven UCR datasets, and a final one covering county-level data, a highly flawed but common use of the UCR data. I highly recommend that you start with the intro chapter (Chapter \@ref(ucr_general)) since it covers topics that apply to each UCR dataset - such as understanding agency unique identifiers and why the data (correctly) has negative numbers - that won't be covered in individual chapters. Each of the UCR dataset chapters will follow the same format: we'll start with a history of the data such as when it first because available and important changes in definitions or variables. We'll then look at which variables are available, and the most important (or most used) ones. The bulk of each chapter will be exploring the data to understand how reliable it is and what questions we can adequately answer using it.

Since manuals are boring, I'll try to include graphs and images to try to alleviate the boredom. That said, I don't think it's possible to make it too fun so sorry in advanced. This book is a mix of facts about the data, such as how many years are available, and my opinions about it, such as whether it is reliable. In cases of facts I'll just say a statement - e.g. "the offenses data is available since 1960". In cases of opinion I'll temper the statement by saying something like "in my opinion..." or "I think" or "I believe."

## Citing this book

If this book was useful in your research, please cite it. To cite this book, please use the below citation: 
    
Kaplan J (2021). *Uniform Crime Reporting (UCR) Program Data: A Practitioner's Guide*. https://github.com/jacobkap/ucrbook. 

BibTeX format:
<pre>
@Book{
    title = {Uniform Crime Reporting (UCR) Program Data: A Practitioner's Guide},
    author = {Jacob Kaplan},
    year = {2021},
    url = {https://ucrbook.com},
  }
</pre>

## Sources of UCR data

There are a few different sources of UCR data available today. First, and probably most commonly used, is the data put together by the [National Archive of Criminal Justice Data (NACJD)](https://www.icpsr.umich.edu/web/pages/NACJD/index.html)). This a team of out of the University of Michigan who manages a huge number of criminal justice datasets and makes them available to the public. If you have any questions about crime data - UCR or other data - I highly recommend you reach out to them for answers. They have a collection of data and excellent documentation available for UCR data available on their site [here](https://www.icpsr.umich.edu/web/NACJD/series/57). One limitation to their data, however, is that each year of data is available as an individual file meaning that you'll need to concatenate each year together into a single file. Some years also have different column names (generally minor changes like spelling robbery "rob" one year and "robb" the next) which requires more work to standardize before you could concatenate. They also only have data through 2016 which means that the most recent years (UCR data is available through 2019) of data are (as of this writing) unavailable. 

Next, and most usable for the general public but limited to researchers, is the FBI's official website [Crime Data Explorer](https://crime-data-explorer.fr.cloud.gov/). On this site you can chose an agency and see annual crime data (remember, UCR data is monthly so this isn't as detailed as it can be) for certain crimes. This is okay for the general public but only provides a fraction of the data available in the actual data so is really not good for researchers. 

Finally, I have my own collection of UCR data [available publicly on openICPSR](https://www.openicpsr.org/openicpsr/search/studies?start=0&ARCHIVE=openicpsr&sort=score%20desc%2CDATEUPDATED%20desc&rows=25&q=jacob%20kaplan%27s%20concatenated%20files), a site which allows people to submit their data for public access. For each of these datasets I've taken the raw data from the FBI (for early years of homicide data this is actually from NACJD since the FBI's raw data is wrong and can't be parsed. For later years of homicide data this is from the FBI's raw data.) and read it into R. Since the data is only available from the FBI as fixed-width ASCII files, I created a setup file (we'll explain exactly how reading in this kind of data works in the next chapter) and read the data and then very lightly cleaned the data (i.e. only removing extreme outliers like an agency having millions of arsons in a month). For each of these datasets I detail what I've done to the data and briefly summarize the data (i.e. a very short version of this book) on the data's page on openICPSR. The main advantage is that all my data has standard variable names and column names and, for data that is small enough, provide the data as a single file that has all years. For large datasets like the arrest data I break it down into parts of the data and not all years in a single file. The downside is that I don't provide documentation other than what's on the openICPSR page and only provide data in R and Stata format. I also have a similar site to the FBI's Crime Data Explorer but with more variables available, that site is available [here](jacobdkaplan.com/).

It's worth mentioning a final source of UCR information. This is the annual Crimes in the United States report released by the FBI each year around the start of October.^[They also release a report about the first 6-months of the most recent year of data before the October release, but this is generally an estimate from a sample of agencies so is far less useful.] As an example, here is the [website for the 2019 report](https://ucr.fbi.gov/crime-in-the-u.s/2019/crime-in-the-u.s.-2019). In this report is summarized data which in most cases estimates missing data and provides information about national and subnational (though rarely city-level) crime data. As with the FBI's site it is only a fraction of the true data available, so is not a very useful source of crime data. Still, this is a very common source of information used by researchers.

## Where to find the data used in this book 

The data I am using in this book is the cleaned (we'll discuss in more detail exactly what I did to clean each dataset in the dataset's chapter, but the short answer is that I did very little.) and concatenated data that I put together from the raw data that the FBI releases. That data is available on my website [here](https://jacobdkaplan.com/data.html). I am hosting this book through GitHub which has a maximum file size allowed that is far smaller than these data so you'll need to go to my site to download the data, it's not available through this book's GitHub repo. For some examples I'm using the data before I cleaned it of outliers (as an example of the outliers present before I removed them) so that data is not publicly available. 

## NIBRS data

Another source of FBI data, and one sometimes considered part of the UCR data collection, is the National Incident-Based Reporting System (NIBRS) data. Like its name implies this is an incident-level dataset which has detailed information about each incident reported to the police, including incident circumstances, and victim and offender information. This is also the data that the FBI has declared will replace UCR data starting in 2021, meaning that they will no longer collect UCR data and only allow agencies to submit NIBRS data. NIBRS data is a complex and highly rich dataset that deserves its own book to really understand, so I will not be discussing it any further in this book.

## This book ... in one paragraph

UCR data is complicated and riddled with limitations, so a naive use of it is certainly wrong. In my opinion, the vast majority of papers that use UCR data should have been rejected. They generally only briefly mention that the data used was UCR data and do not discuss issues with the data such as under-reporting, imputation procedures, or missing data. While their results may not change (or at least not change enough to affect the results) once they account for this, the lack of even bothering to discuss these issues is enough of an issue for an immediate desk reject. Surprisingly, this problem is even more severe for the worst UCR data, county-level imputed data and hate crime data, demonstrating that the authors who use that data are generally the ones least qualified (otherwise they wouldn't use it at all) to do so.

## How to contribute to this book

If you have any questions, suggestions, or find any issues, please email me at jkkaplan6 [@] gmail.com. For more minor issues like typos or grammar mistakes, you can edit the book directly through its GitHub page. That'll make an update for me to accept, which will change the book to include your edit. To do that, click the edit button at the top of the site - the button is highlighted in the below figure. You will need to make a GitHub account to make edits. When you click on that button you'll be taken to a page that looks like a Word Doc where you can make edits. Make any edits you want and then scroll to the bottom of the page. There you can write a short (please, no more than a sentence or two) description of what you've done and then submit the changes for me to review.

<img src="images/edit_button.PNG" width="346" />

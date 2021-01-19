## Research blog
 
### This blog keeps track of my research of defaced web pages.

** 06/02/2020 **
Start importing blog entries

### 13/02/2020
The first round of scoping material is well underway. From what I can say now, about 3% of the total material is in scope. Looking at a dataset of approx. 15000 pages at the moment, this means about 450 defaced web sites to be in scope. This is a consequence of the initial inverse (from old to new) crawl. As defacements are usually submitted in bulks, there are always huge chucks of non-qualifying defacements found. To meet with supervisor to discuss a more focused approach. 

## 04/03/2020
The first round of scoping is completed and first tests on data extraction have been run. I am using the Natural Language Toolkit for Python to clean and analyze the pages. There is the idea of moving on to SQL to manage the data  more efficiently. 

## 09/04/2020
I have moved the whole structure to an SQL database. This allows my data to be arranged with more flexibility, so that I can run queries such as word count over time. It also expands the capacity of my system, as SQL can manage much more data than the previous CSV-file approach. There were a few difficulties in using Text Analysis with SQL, all grounded in the idea that SQL is a relational database (One field relating to one value) while a tokenized text of course has many different fields (words and their appearance). Initially I tried to solve this by storing my tokens as JSON objects in SQL and then retrieving them to use in Python but this was too clumsy and required too much back and forth changing of data from JSON to list to a dataframe. Instead, the current solution stores the whole text as a single object in SQL together with the timestamp, then Python retrieves that object and timestamp, tokenizes it and converts it into a Pandas dataframe for analysis. 

Currently the scraping goes on because I want to capture defacements around 9/11. About 12.000 pages captured so far with approx. 400 relevant defacements.

## 30/06/2020
Scraping has been completed shortly after the last post. I ran into the issue that later defacements had a high number of invalid submissions among them. Those invalid submissions would slow down the crawl considerably. My solution was the following:
    If an invalid page is enountered:
        Pick a random number between 1 and 10 and skip forward
        If after two skips, the crawler still only sees invalid pages:
            Pick a random number between 11 and 100 and skip forward
This has worked well and cleared the chunks of invalid pages without loosing too much content.

I have written the first draft of my first case study of defacements submitted in the context of the Kashmir conflict. The chapter draws upon quantitative data from the scraping process as well as qualitative, emblematic defacements. 

There was little context mentioning WikiLeaks, while I initially expected there to be much more. I wrote a chapter about it, trying to place a cybercrime archive like Zone-H in relation to WikiLeaks and find hints for the strange distance they kept.

## 19/01/2021
A long overdue update. Status so far:
 Case Study 1 - Pending feedback
 Case Study 2 - Reviewed and ready
 Case Study 3 - Pending final review
 Wikileaks chapter - Pending final review
 
Additionally, I developed a graphical user interface version of the crawler. I am afraid it is less useful than the command-line based version because it is less flexible but I hope it makes my work a bit more accessible. 


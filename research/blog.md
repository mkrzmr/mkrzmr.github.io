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

## 15/04/2020
   “There are decades where nothing happens; and there are weeks where decades happen.” 
   
Currently very happy to have a load of desk work to do for the analysis. 

I have now moved onto collect defacements from the 22nd of October 2010 on. That day, the largest document leak in US military history occurred when Wikileaks published 391,832 US army field reports. The leak was known as the Iraq War Logs and documented the death of an additional 15.000 civilians, bringing the total number of deaths up to 150,000. 
My research is now looking at the intersection between this event and web defacements. From a technical side, I am facing the problem of many <50% invalid defacement Ids. This slows down the crawl. Instead of moving up in steps of 1, I might have to change my crawler to moving in batches of 100 to skip through invalid Ids. An idea would be:

	Valid page found? → move up 1 to next page
	Invalid page found? → move up by 10 to try and escape batch of invalid IDs
		still invalid? Go up another 10
			still invalid? Jump by 100


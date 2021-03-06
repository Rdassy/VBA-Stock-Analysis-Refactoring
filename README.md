# VBA Experimentation: Refactoring Stock Analysis Script


## Overview of Project: Explain the purpose of this analysis.

The purpose of this project was to improve and build upon a workbook we had created to analyze stock market data.  
  
Initially, our workbook would loop through a dataset comprised of tickers along with their respective prices and trading volumes for a set date. The data we were provided with was split between two worksheets by year for 2017 and 2018.  

We created a macro to loop through the stock market data and gather the total daily volume and total return for each ticker. To make this easy to use for any user, we tied the macro to a button which would prompt the user to enter which year they wish to analyze before populating a worksheet with the aforementioned data.  
  
While this macro worked fine when using a limited dataset of only 12 tickers, one may wonder if the script is written in an efficient manner that would allow it to loop through a dataset that includes many more tickers or even the stock market as a whole.

After adding a timer to the macro to see how long it took to run the script for the years 2017 and 2018 of this dataset, we found the run time was actually pretty slow and could likely be refactored to run faster and more efficiently.

Once this was accomplished, we could then dive into the data analysis produced by our script and compare the stocks performance between 2017 and 2018.  
  
  
## Results: Using images and examples of your code, compare the stock performance between 2017 and 2018, as well as the execution times of the original script and the refactored script.

### Refactoring

The original script for 2017 and 2018 ran quite slow:

![Pre_Refactor_2017_Timer](https://user-images.githubusercontent.com/76575162/117553550-e9e88c00-b017-11eb-8d32-d633b6bd8b44.png)
![Pre_Refactor_2018_Timer](https://user-images.githubusercontent.com/76575162/117553559-ec4ae600-b017-11eb-99a3-9c3eae7a5623.png)


After refactoring, the script ran a lot faster and we obtained a much quicker execution time:

![Post_Refactor_2017_Timer](https://user-images.githubusercontent.com/76575162/117553572-f836a800-b017-11eb-8f5b-3ae6dd6f09b7.png)
![Post_Refactor_2018_Timer](https://user-images.githubusercontent.com/76575162/117553575-f967d500-b017-11eb-84af-1782574a9b87.png)


While most of the original script was the same as the refactored script, the "For" loop going through the data is actually a little inefficient in the original script as it contains a nested "For" loop which causes a lot more operations than needed. Here is a comparison between the two loops:

![Pre_Refactor_Loop_Code](https://user-images.githubusercontent.com/76575162/117553601-2ae0a080-b018-11eb-8e69-f7bcfa0ebdf6.png)
![Post_Refactor_Loop_Code](https://user-images.githubusercontent.com/76575162/117553610-33d17200-b018-11eb-9f05-50494c0aca11.png)

The biggest difference between the two is that by using a new variable as an index for tickers called "tickerIndex", we were able to get rid of the nested "For" loop and greatly reduce the amount of operations initiated by the script. Going from a 0.50s run time to 0.067 means that our changes made the script run almost 10 times quicker. This would mean that the time savings would be considerable when using this script with much larger data sets.

While the results of these tests were obviously showing a large processing time reduction, please keep in mind that the user's hardware matters greatly when it comes to how fast the scripts run and that the results we obtained may not match yours. 

Lastly, it is also important to note that to help visualize the analysis results with a lot more clarity, the refactored script also included a formatting section to be ran after the data loops to change the appearance of cells depending on values. This may have caused the script to run a bit slower but probably by a negligible amount.

### Stocks Performance

As shown in the images below, 2018 was not nearly as good a year as 2017 for the stocks included in our data set:

![Stock_Performance_2017_Table](https://user-images.githubusercontent.com/76575162/117553623-4186f780-b018-11eb-9682-7994cc7589bd.png)
![Stock_Performance_2018_Table](https://user-images.githubusercontent.com/76575162/117553624-4350bb00-b018-11eb-8765-506a35a8e88a.png)


Among all the tickers tracked, only ENPH and RUN showed continued growth and did so by quite a large margin; both stocks rose over 80% year over year and saw their total daily volume explode (close to 3X for ENPH and 2X for RUN) while most other stocks were close to the same or regressed. The only exception is DQ, which after a great 2017 and relatively low trading volumes lost 62.6% in 2018 with close to triple the closing volume

Most other stocks lost value in 2018, but it would be good for this analysis to include more years worth of data along with macro market trends to make any recommendations for which stocks to invest in.
  
  

## Summary:

### What are the advantages or disadvantages of refactoring code?

In this case, refactoring code allows users to find inefficiencies in the original code to make it run faster. One of the most important things about refactoring is that it would allow someone to improve upon existing code rather than writing it from scratch and testing it themselves (assuming the original code works), resulting in less time spent on code development. Additionally, if code is improved to run faster by spending a bit of time refactoring it, it results in a compounding effect for the time saved by the users running the code multiple times down the line.

It is also possible to refactor the code to make it easier to understand, improve the design of software and help find bugs. 

On long-term projects, refactoring is an essential tool for software maintenance so long as it is within the confines of the project's time and budget constraints. 

Refactoring the code could result in software malfunction or cause confusion for other programmers, highlighting the importance of tracking modifications and having enough comments to help others navigate the code. 

(used [this page](https://stackoverflow.com/questions/43983284/what-are-the-advantages-and-disadvantages-of-refactoring-code-smell-in-software) as a source for complementary info)


### How do these pros and cons apply to refactoring the original VBA script?

The scope of this project is very minimal as this is a small VBA script rather than a large piece of software. The main focus of refactoring this subroutine was to improve its efficiency so that large data sets would not take too long to be analyzed.

The time savings caused by the refactoring will likely end up compounding down the line as it now runs 10 times faster for out test data set. The inclusion of comments throughout the code explaining which steps were taken improve efficiency for this script could be a guide for whomever ends up wanting to improve upon it later on.  

As this data set was already sorted in a particular fashion, we did not need to include a sorting segment in the script in order for it to run smoothly. However, if someone were to run this script on a much larger data set that is not sorted by ticker and by date, it is likely that it would not work.  

As this was not in the scope of this project, this will be a task for the next person who wants to refactor this script.

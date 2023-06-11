# Am I The Asshole: An Important Question Turned Into A Data Science Project 

**Note: This is an old project from Fall 2020 when I took DSCI 511 (Data Acquisition and Pre-Processing).**

## Project Description
The objective of this project was to create a dataset. I used Reddit's API to collect responses from [r/AmITheAsshole](https://www.reddit.com/r/AmItheAsshole/). To run this code, you need PRAW API keys, which you can [learn about here.](https://praw.readthedocs.io/en/stable/)


Disclaimer: I flew too close to the sun and messed up this project. I will eventually come back and fix this, but for now, I'm posting the project as is. If anything, this repository is great representation of the stress and chaos that was Fall 2020. IYKYK. 

---
## Contents 

#### Code
There are 4 python notebook files that contain all the code. They should be ran in consecutive order.

1. **Part1a-AcquiringPostID.ipynb:** this file uses pushshift to collect the post IDs for the desired range of posts.  
    - It saved the 700,000+ ids as "postIDs.json" in the data folder. 
2. **Part2-CreateDataset.ipynb:** this file uses PRAW to gather more specific information about the posts using the post id/link. 
    - Make sure to input your own PRAW keys
    - Given the size of the data from 1a, it would've taken my computer 6 days to run this part so I reduced it to 70,000 posts. However, I messed up and only saved the posts that had a verdict or weren't deleted, so 13 hours later I found out it only ran up to 39,000 posts and out of these it only saved 114 posts. That is why I had to add in data from 2b. This increased my dataset to almost 1000 posts. 
    - (I saved the data every 1000 iterations in case it terminated early since it was running all night)
3. **Part2b-AddingMoreData.ipynb:** this file uses query to search for the flair (aka verdict) on the subreddit. I was able to get 200+ posts for each category, totaling in 800 posts.
    -  These posts are all within the last couple months, whereas the posts from 1a are between 2015-2018. Note that links/ids are both unique identifiers that I can use for part 2 so it doesn't matter which one I collect. The links are all saved in the folder "data-big" as 4 separate json files. 
4. **Part3-CleaningData.ipynb:** this file uses the "temporaryData_39000.csv", "YTA.csv" , "NTA.csv" "ESH.csv" and "NAH.csv" files and merges/cleans them. The outputted data is "Data_cleaned.csv" 


#### Data
- **postIDs.json:** all the post IDs for the specified posts. There are over 700,000 ids. 
- **temporaryData_x.csv:**  where x is the number of posts processed. There are 39 data files but you should only care about the last one, temporaryData_39000.csv. This is from part 2 containing the post with their features. 
- **Data_cleaned.csv:** the cleaned, finalized data! 

In the big-data folder:

contains links to posts with YTA, NTA, ESH, and NAH verdicts from 2b
- YTA_big_links.json 
- NTA_big_links.json 
- ESH_big_links.json
- NAH_big_links.json

saved datasets with YTA, NTA, ESH, and NAH verdicts from 2b
- YTA.csv 
- NTA.csv 
- ESH.csv  
- NAH.csv 


---
## Limitations
-In total, this code takes 15 hours to run and since I only have 1 computer I was very limited. I was rushed because every time I made a mistake I would add another day of just the code running. If I could do it again, I'd get another team member just so we could have a computer to dedicate solely to running the code. 

-The data in 2b is slightly different from 1 so I had to modify the awards columns. This is because I worked on 2b before 1 and thought it would be a good idea to record the awards given. However, as I increased the size of the data I realized this is infeasible for my time constraint. 

-In 2b I have code for tallying the votes in the comments, but for the thousands of posts and comments, this would've take my computer way too long to process. 

-Initially I did this whole thing without APIs and only using BeautifulSoup. However it took WAY longer and I would not recommend it. But it is possible!





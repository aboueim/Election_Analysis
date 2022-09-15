# Election Analysis Challenge

## Overview of Project

A Colorado board of elections employee has asked me to fulfill the following tasks to complete the election audit of a recent local congressional election.

Tasks:

To identify

1. The voter turnout for each county
2. The percentage of votes from each county out of the total count
3. The county with the highest turnout

The results of the project also provides:

- The total number of votes cast in the precint.
- A complete list of candidates who received votes.
- The total number of votes each candidate received.
- The percentage of votes each candidate won.
- The winner of the election based on popular votes.

## Analysis

### Python Code

Following represents the script for the election audit:



## Election-Audit Results:

### Election Audit Result in VS Code Terminal

![This is an image](/Terminal_Output.png)



### Election Audit Result in VS Code Terminal

![This is an image](/election_results_write.png)


## Results Summary

The analysis of the election shows that:

- There were **369,711** votes cast in the election.

- The election was held in three counties as following:

    Jefferson
    Denver
    Arapahoe

- The county results were:

    Jefferson comprised 10.5% of the voters and 38,855 number of the votes.
    Denver comprised 82.8% of the votes and 306,055 number of the votes.
    Arapahoe comprised 6.7% of the votes and 24,801 number of the votes.
    
- The county with the largest voter turnout was:

    Denver that comprised 82.8% of the votes and 306,055 number of the votes.
    
- The candidates were:

    Charles Casper Stockham
    Diana DeGette
    Raymon Anthony Doane

- The candidate results were:

    Charles Casper Stockham received 23.0% of the votes and 85,213 number of the votes.
    Diana DeGette received 73.8% of the votes and 272,892 number of the votes.
    Raymon Anthony Doane received 3.1% of the votes and 11,606 number of the votes.

- The winner of the election was:

    Diana DeGette, who received 73.8% of the votes and 272,892 number of the votes.

## Election-Audit Summary: 

The script developed for the purpose of the above election audit can be utilized in order to replicate such analysis for similar elections in other regions. The script works based on how the election dataset used to store election data is structured and can iterate through the entire dataset regardless the number of records stored. Thus, if the same data structure (it means, first column as Ballot IDs, second column as County names, ad third columns as Candidate name) is used to store data related to other elections, the existing code can simply run the same analysis and give expected results. However, even if the dataset does not follow exatly the same structure, the script is strill valid for election audit. For example, in case the column order is changed or new columns are added, simply modifying index numbers, one can obtain correct results.



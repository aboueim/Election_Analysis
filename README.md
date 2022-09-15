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



### Election Audit Result Printed in a Text File

![This is an image](/election_results_write.png)


## Results Summary

The analysis of the election shows that:

- There were **369,711** votes cast in the election.

- The election was held in three counties as following:

    1. **Jefferson**
    2. **Denver**
    3. **Arapahoe**

- The county results were:

    Jefferson county comprised **10.5%** of the voters and **38,855** number of the votes.
    Denver county comprised **82.8%** of the votes and **306,055** number of the votes.
    Arapahoe county comprised **6.7%** of the votes and **24,801** number of the votes.
    
- The county with the largest voter turnout was:

    Denver that comprised 82.8% of the votes and 306,055 number of the votes.
    
- The candidates were:

    **Charles Casper Stockham**
    **Diana DeGette**
    **Raymon Anthony Doane**

- The candidate results were:

    * Charles Casper Stockham received **23.0%** of the votes and **85,213** number of the votes.
    * Diana DeGette received **73.8%** of the votes and **272,892** number of the votes.
    * Raymon Anthony Doane received **3.1%** of the votes and **11,606** number of the votes.

- The winner of the election was:

    **Diana DeGette**, who received **73.8%** of the votes and **272,892** number of the votes.

## Election-Audit Summary: 

The script developed for the purpose of the above election audit can be utilized in order to replicate such analysis for similar elections in other regions. The script works based on how the election dataset used to store election data is structured and can iterate through the entire dataset regardless the number of records stored. Thus, if the same data structure (it means, first column as Ballot IDs, second column as County names, ad third columns as Candidate name) is used to store data related to other elections, the existing code can simply run the same analysis and give expected results for as many candidate and county as included. However, even if the dataset does not follow exatly the same structure, the script will be still valid to audit the election. For example, in case the column order is changed or new columns are added, simply by modifying index numbers, one can obtain correct results. Assume candidate name was stored in the fourth column (i.e., Column D), then switching candidate name index from 2 to 3 would lead us to proper results.

 Get the candidate name from each row.
 candidate_name = row[3]

Besides, the reporting style is also almost dynamic. That is, no matter the number of candidates or counties, the script always appends all the candidate names and county names to defined lists and reports the corresponding vote percentage and numbers. Therefore, the election board does not need to customize the output format for each new election. However, if additional comments or different titles are needed, they simply can rewrite the f-strings embedded in the script to change the static texts. For example, the board can rename the title of the report to "Western Counties Election Results" by adding "Western Counties" to the following

Standard format:

 election_results = (
        f"\nElection Results\n"
     ....
     
Updated format:

 election_results = (
        f"\nWestern Counties Election Results\n"
        
 
 Overall, the script follows a flexible logic for calculating vote percentage and numbers for different candidates and counties as it uses both solid mathematical conditions and has the ability to iterate through different datasets with similar structures. Given that, it is suggested that the election committee use this script as a basis for auditing other elections ahead.

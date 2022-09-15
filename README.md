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

Note: a "!" is added before the "#" where the comments could turn to a header in the .md file. The original .py file is uploaded to the repository entitled PyPoll_Challenge.py.

!# -*- coding: UTF-8 -*-
"""PyPoll Homework Challenge Solution."""

!# Add our dependencies.
import csv
import os

!# Add a variable to load a file from a path.
file_to_load = os.path.join("Resources", "election_results.csv")
!# Add a variable to save the file to a path.
file_to_save = os.path.join("analysis", "election_results.txt")

!# Initialize a total vote counter.
total_votes = 0

!# Candidate Options and candidate votes.
candidate_options = []
candidate_votes = {}

!# 1: Create a county list and county votes dictionary.

counties = []
counties_votes = {}

!# Track the winning candidate, vote count and percentage
winning_candidate = ""
winning_count = 0
winning_percentage = 0

!# 2: Track the largest county and county voter turnout.

largest_turnout_county = ""
largest_turnout_county_votes = 0
largest_turnout_county_percentage = 0

!# Read the csv and convert it into a list of dictionaries
with open(file_to_load) as election_data:
    reader = csv.reader(election_data)

    # Read the header
    header = next(reader)

    # For each row in the CSV file.
    for row in reader:

        # Add to the total vote count
        total_votes = total_votes + 1

        # Get the candidate name from each row.
        candidate_name = row[2]

        # 3: Extract the county name from each row.
        counties_name = row[1]

        # If the candidate does not match any existing candidate add it to
        # the candidate list
        if candidate_name not in candidate_options:

            # Add the candidate name to the candidate list.
            candidate_options.append(candidate_name)

            # And begin tracking that candidate's voter count.
            candidate_votes[candidate_name] = 0

        # Add a vote to that candidate's count
        candidate_votes[candidate_name] += 1

        # 4a: Write an if statement that checks that the
        # county does not match any existing county in the county list.
        if counties_name not in counties:
        
            # 4b: Add the existing county to the list of counties.
            counties.append(counties_name)

            # 4c: Begin tracking the county's vote count.
            counties_votes[counties_name] = 0

        # 5: Add a vote to that county's vote count.
        counties_votes[counties_name] += 1

!# Save the results to our text file.
with open(file_to_save, "w") as txt_file:

    # Print the final vote count (to terminal)
    election_results = (
        f"\nElection Results\n"
        f"-------------------------\n"
        f"Total Votes: {total_votes:,}\n"
        f"-------------------------\n\n"
        f"County Votes:\n")
    print(election_results, end="\n")

    txt_file.write(election_results)

    # 6a: Write a for loop to get the county from the county dictionary.
    for counties_name in counties_votes:

        # 6b: Retrieve the county vote count.
        votes_counties = counties_votes.get(counties_name)

        # 6c: Calculate the percentage of votes for the county.
        votes_counties_percentage = float(votes_counties)/float(total_votes) * 100
        counties_results = (
            f"{counties_name}: {votes_counties_percentage:.1f}% ({votes_counties:,})\n")

         # 6d: Print the county results to the terminal.
        print(counties_results, end="\n")
        
         # 6e: Save the county votes to a text file.
        txt_file.write(counties_results)

         # 6f: Write an if statement to determine the winning county and get its vote count.
        if (votes_counties > largest_turnout_county_votes) and (votes_counties_percentage > largest_turnout_county_percentage):
            largest_turnout_county_votes = votes_counties
            largest_turnout_county = counties_name
            largest_turnout_county_percentage = votes_counties_percentage

    # 7: Print the county with the largest turnout to the terminal.
    county_results = (
        f"\n-----------------------\n"
        f"Largest County Turnout: {largest_turnout_county}\n"
        f"-----------------------\n"
        )
    print(county_results, end="\n")

    # 8: Save the county with the largest turnout to a text file.
    txt_file.write(county_results)

    # Save the final candidate vote count to the text file.
    for candidate_name in candidate_votes:

        # Retrieve vote count and percentage
        votes = candidate_votes.get(candidate_name)
        vote_percentage = float(votes) / float(total_votes) * 100
        candidate_results = (
            f"{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n")

        # Print each candidate's voter count and percentage to the
        # terminal.
        print(candidate_results)
        #  Save the candidate results to our text file.
        txt_file.write(candidate_results)

        # Determine winning vote count, winning percentage, and candidate.
        if (votes > winning_count) and (vote_percentage > winning_percentage):
            winning_count = votes
            winning_candidate = candidate_name
            winning_percentage = vote_percentage

    # Print the winning candidate (to terminal)
    winning_candidate_summary = (
        f"-------------------------\n"
        f"Winner: {winning_candidate}\n"
        f"Winning Vote Count: {winning_count:,}\n"
        f"Winning Percentage: {winning_percentage:.1f}%\n"
        f"-------------------------\n")
    print(winning_candidate_summary)

    # Save the winning candidate's name to the text file
    txt_file.write(winning_candidate_summary)

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

    * Jefferson county comprised **10.5%** of the voters and **38,855** number of the votes.
    * Denver county comprised **82.8%** of the votes and **306,055** number of the votes.
    * Arapahoe county comprised **6.7%** of the votes and **24,801** number of the votes.
    
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

The script developed for the purpose of the above election audit can be utilized in order to replicate such analysis for similar elections in other regions. The script works based on how the election dataset used to store election data is structured and can iterate through the entire dataset regardless the number of records stored. Thus, if the same data structure (it means, first column as Ballot IDs, second column as County names, ad third columns as Candidate name) is used to store data related to other elections, the existing code can simply run the same analysis and give expected results for as many candidate and county as included. However, even if the dataset does not follow exatly the same structure, the script will be still valid to audit the election. For example, in case the column order is changed or new columns are added, simply by modifying list index numbers, one can obtain correct results. Assume candidate name was stored in the fourth column (i.e., Column D), then switching candidate name list index from 2 to 3 would lead us to proper results.

Standard format:

 Get the candidate name from each row.
 candidate_name = row[2]

Updated format:

Get the candidate name from each row.
 candidate_name = row[3]


Besides, the reporting style is almost dynamic. That is, no matter the number of candidates or counties, the script always appends all the candidate names and county names to defined lists and reports the corresponding vote percentage and numbers in consecutive lines. Therefore, the election board does not need to customize the output format for each new election. However, if additional comments or different titles are needed, they simply can rewrite the f-strings embedded in the script to change the static texts. For example, the board can rename the title of the report to "Western Counties Election Results" by adding "Western Counties" to the following script.

Standard format:

 election_results = (
        f"\nElection Results\n"
     ....
     
Updated format:

 election_results = (
        f"\nWestern Counties Election Results\n"
        
 
 Overall, the script follows a flexible logic for calculating vote percentage and numbers for different candidates and counties as it uses both solid mathematical conditions and has the ability to iterate through different datasets with similar structures. Given that, it is suggested that the election committee use this script as a basis for auditing other elections ahead.

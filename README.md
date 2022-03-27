# Unix - Grep


## Accompanying resources
* [Perl Compatible Regular Expression Docs](https://www.pcre.org/current/doc/html/pcre2pattern.html)
* [PCRE Cheatsheet](https://www.debuggex.com/cheatsheet/regex/pcre)


## Daily Event Log

Inside of the data directory there is a file called "transaction_data_daily_event_log_20190129.dat". This file represents a log generated by a device such as a gas pump or a vending machine. Every two hours it initiates an upload of its transaction data. The device logs the time it attempted to initiate a transfer as well as the outcome of each attempt.

Use grep to find all instances where the upload was initiated. 
```
PROVIDE A SOLUTION HERE
grep -e  "start"  transaction_data_daily_event_log_20190129.dat


Once you've reviewed these results, repeat the process but this time using the -c flag to determine how many matching occurences were found.


```
PROVIDE A SOLUTION HERE

grep -c  "start"  transaction_data_daily_event_log_20190129.dat
12
```


Use grep to find all instances where the upload was successful. 
```
PROVIDE A SOLUTION HERE

grep -e  "complete"  transaction_data_daily_event_log_20190129.dat
DIDLM230::transaction_data_upload_complete_00_20190129_000053
DIDLM230::transaction_data_upload_complete_01_20190129_020035
DIDLM230::transaction_data_upload_complete_02_20190129_040015
DIDLM230::transaction_data_upload_complete_03_20190129_060124
DIDLM230::transaction_data_upload_complete_04_20190129_083522
DIDLM230::transaction_data_upload_complete_05_20190129_102311
DIDLM230::transaction_data_upload_complete_06_20190129_121750
DIDLM230::transaction_data_upload_complete_07_20190129_141306
DIDLM230::transaction_data_upload_complete_08_20190129_161148
DIDLM230::transaction_data_upload_complete_09_20190129_180912
DIDLM230::transaction_data_upload_complete_10_20190129_200405
DIDLM230::transaction_data_upload_complete_11_20190129_220110
```

Once you've reviewed these results, determine how many matching occurrences were found. This time instead of using the -c flag, pipe the result to the wc program.
```
PROVIDE A SOLUTION HERE

grep -e  "complete"  transaction_data_daily_event_log_20190129.dat | wc
      12      12     744


```



Use grep to find all instances where the upload failed. Ensure your output displays the line numbers for each match.

```
PROVIDE A SOLUTION HERE

grep -e  "fail"  transaction_data_daily_event_log_20190129.dat    
DIDLM230::transaction_data_upload_failure_04_20190129_080133::WEAKSIGNAL
DIDLM230::transaction_data_upload_failure_06_20190129_120000::SYSTMAINTE
DIDLM230::transaction_data_upload_failure_07_20190129_140754::WEAKSIGNAL
DIDLM230::transaction_data_upload_failure_09_20190129_180000::SYSOFFLINE

```

Upon review, we would like to only view failures with error code SYSOFFLINE or WEAKSIGNAL.

```
PROVIDE A SOLUTION HERE

grep -E  "WEAKSIGNAL|SYSOFFLINE"  transaction_data_daily_event_log_20190129.dat 
DIDLM230::transaction_data_upload_failure_04_20190129_080133::WEAKSIGNAL
DIDLM230::transaction_data_upload_failure_07_20190129_140754::WEAKSIGNAL
DIDLM230::transaction_data_upload_failure_09_20190129_180000::SYSOFFLINE
```


## Dunder Mifflin Paper Co. Users

Inside the data directory, there is a file called "users.csv". This file contains details of users registered to an email subscription service provided by Dunder Mifflin paper company. 

Identify users that have email addresses with six or less characters before the @ symbol where none of these characters are numbers.
```
PROVIDE A SOLUTION HERE
```


Marketing research has shown that the paper business is picking up in the academia space. Corporate has requested a list of all registered users that have an edu emaill address. Use grep to find the appropriate lines and output the results to a file called academia_users.txt.
```
PROVIDE A SOLUTION HERE
```


Ryan Howard did a poor job and used the CC field rather than the BCC field for the company's email campaign. Dwight received a tip from Jim that there is a registered user who exploided this oversight to poach clients from Dunder Mifflin Paper Co. Dwight has provided us with two pieces of information:
1. The user registed to the service from an IPV4 ip address starting with the numbers 184. 
2. The user's phone number starts with the numbers 38.

Use grep to identify the user with a single regex pattern.
```
PROVIDE A SOLUTION HERE
```


## Dunder Mifflin Is Hiring

After Ryan Howard's demotion for mishandling of sensitive data, Dunder Mifflin is searching for a proper software developer. While they are open to hiring a remote worker, they would like someone who resides within the state of Pennsylvania.

You have been provided with two sample tab delimited files inside the data folder. The sample files are named "candidates_1.txt" and "candidates_2.txt" and they contain information about various individuals who are open to hearing about a new career opportunity. You will continue to receive files like this daily until the position is filled.

Each entry in the provided files will contain the following details about a potential hire:
* id
* first_name
* last_name
* job_title
* city
* state

This regex expression will ultimately be part of an automated data pipeline so we want it to be as hardened as we can reasonably make it. Write a regex expression that meets the following constraints.

* Starting and ending anchors for each line.
* Each entry will have an id of one or more digits
* Last names must begin with an upper case letter (a-z).
* Last names may contain any number of characters (a-z). It may also contain spaces, dashes, and hyphens.
* First names must begin with an upper case letter (a-z).
* First names may contain any number of characters (a-z). It may also contain spaces, dashes, and hyphens.
* A candidate's current job title must contain the word "Software" and/or "Developer".
* City must not contain any digits.
* Each field must be separated by a tab character.

```
PROVIDE A SOLUTION HERE
```

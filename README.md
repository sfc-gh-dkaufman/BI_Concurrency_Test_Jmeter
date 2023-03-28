# BI Concurreny Test using Jmeter

This project shows you how you can use Jmeter to perform a simple concurrency test against your SQL platform to simualate high concurrecy workloads often generated by BI tools like Tableau, pwoerBI, Thoughtspot & ,etc.

## What do we measure?

1. We will be executing a series of queries joining 3 tables together where the largest table is 60M rows. 
2. Each Query will have a unique WHERE filter clause to make sure each one is filtering on a unique set of values with varying resultsets.
3. Each query will have a RANDOM() function is the SELECT column list to make sure servers are not using any previously cached results and executing each query every.
4. Jmeter will be configured Ramp-Up from 0-100 queries within the 1st 60 secs in 6 steps (~16 queries each time) and hold 100 queries for another 1 minute.
5. We will measure
    - **Total number of queries** executed in the 2 minute run time (Throughput)
    - **Average Execution times** per query. (Performance)
    - **% of Errors** overall during the test (# of failed queries due to high concurrency)
  
## How do we test it?
Please refer to my [Medium blog page](https://www.google.com) for details around performing this test using Snowflake & the Sample TPCH data. You can use other datasets & platforms as well using the similar steps.

## Resoure Files needed for this test

1. Install **Apache Jmeter**. [Download Here](https://jmeter.apache.org/download_jmeter.cgi)
2. **Jmeter BZM Concurrency Plugin** [Download here](https://medium.com/r?url=https%3A%2F%2Fjmeter-plugins.org%2Ffiles%2Fpackages%2Fjpgc-casutg-2.10.zip). 
    - To install simply unzip the file and copy the contents to Jmeter_Install_Path\lib\ folder. Once done:
      - **jmeter-plugins..0.6.jar** should be directly in the **\Jmeter_Install_Path\lib\**  
      - The files in **\ext\** subfolder of the zip should be in **\Jmeter_Install_Path\lib\ext\** 
3. **Concurrency_Test_Snowflake_Public.jmx** Jmeter test file to run against Sample Snowflake TPCH dataset.  [Download here]()
4. **Search_Filters.csv** file which has a list of valid search value combinations that will be used to contruct unique queries. [Download here]()

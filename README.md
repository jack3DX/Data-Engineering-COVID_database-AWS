# Data Engineering project with COVID data and AWS tools

In this repository, I'll show my data engineering project on the COVID numbers. It will be divided into the following steps:
- Data storage in S3 (the dataset comes from AWS open dataset)
- Crawler creation to extract and examine the schemas and data formation
- Use of AWS Athena to run some queries (like SQL)
- Use of AWS Glue to transform the data and the store it into the data warehouse
- Check if the data is available to use in the visualization tools


- **I'll probably create another repository to show the visualization of this data** </br>
- **The ideia for this project was found in the web** </br>

## The dataset

The dataset for this project may be found on AWS website, [in this link](https://s3.console.aws.amazon.com/s3/buckets/covid19-lake/?region=us-east-2&tab=objects).</br>
There's some additional information about this data on AWS blog [post](https://aws.amazon.com/pt/blogs/big-data/a-public-data-lake-for-analysis-of-covid-19-data/#:~:text=The%20AWS%20COVID%2D19%20data,all%20the%20available%20data%20sources.) .

The ones I copied to my bucket in S3 were:
- enigma-jhu/
- enigma-nytimes-data-in-usa/
- rearc-covid-19-testing-data/
- rearc-usa-hospital-beds/
- static-datasets/

As they don't permit any kind of copy or synchronization, the process has to be manual.

I used the following command in cmd, once I got to the path I stored the folders: aws s3 cp . s3://de-covid-raw-dev/ --recursive 

## Extracting schema and information

For this step, AWS Crawler must be used. I've opened AWS Glue and went to the Crawlers section and created one with the following settings:
- name: de-covid-enigma-jhu-crawler
- source type: data stores (as I want it to create the tables from scratch)
- crawl all folders
- data store: S3
- path: s3://de-covid-raw-dev/enigma-jhu/csv
- role: one I had created with roles of S3FullAccess, GlueConsoleFullAccess and GlueServiceRole
- Run on demand
- database: created one name covid19-database

It ran ok. Opening Athena, I could already Query some information about it:

![alt text](https://github.com/jack3DX/Data-Engineering-COVID_database-AWS/blob/main/images/FirstQuery.PNG?raw=true)

As I saw it working, I had to insert some prefix names to the table, because the process need to be done for every bucket.

![alt text](https://github.com/jack3DX/Data-Engineering-COVID_database-AWS/blob/main/images/TableNamePrefix.PNG?raw=true)

Then I proceeded to add crawlers for every bucket. The final list is presented in the image below:

![alt text](https://github.com/jack3DX/Data-Engineering-COVID_database-AWS/blob/main/images/CrawlersList.PNG?raw=true)

# Model conversion

The next step is to convert the relational datamodel (which is present in the Tables of Glue) into a dimensional, to be able to transform and write scripts accordingly to build the data warehouse. 

On a star schema, the best arrangement I've found is to put Covid as the fact table and hospital, region and date as dimensions. If you're following this project, do it yourself as an exercise.

Also, if you need a flowchart maker, I suggest using draw io, which may also be found as diagrams.net.

The next steps were done in a jupyter notebook, which is in this repository.



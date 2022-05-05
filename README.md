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

The steps are the following:
- Select the buckets and look for the same option as in the image below:

![alt text](https://github.com/jack3DX/Data-Engineering-COVID_database-AWS/blob/main/images/CopyingPublicDatasets.png?raw=true)



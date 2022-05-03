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

The dataset for this project may be found on AWS website, [in this link](https://aws.amazon.com/pt/covid-19-data-lake/).</br>
There's some additional information about this data on AWS blog [post](https://aws.amazon.com/pt/blogs/big-data/a-public-data-lake-for-analysis-of-covid-19-data/#:~:text=The%20AWS%20COVID%2D19%20data,all%20the%20available%20data%20sources.) .

In the blog post, there's also a link that opens AWS S3 explorer, where is possible to see all the contents and tables of this data. As read in it, the data is presented at "enigma-jhu"


# DataEnginneringWithADF

Project:- Data Engineering with Azure Data Factory - Weekend project on Covid-19 <br>

During the weekend I've created a Data Engineering project using Azure Data Factory just for fun.
The project shows Population Data, Testing Done till the available Date, Hospital admissions, No. of active cases, Total No. of cases & Deaths. I will be improving upon this project by adding more countries to it with credible data sources that I can find for the above-given Parameters & will be adding! more parameter of "No. of People vaccinated till date".
If you guys know such sources please comment below & do leave your reviews.
It was fun creating a fully automated ETL Task as well as creating Data pipelines on azure and visualizing them on PowerBI.

Github Link:- https://github.com/Yashmalhotra98/DataEnginneringWithADF

PowerBI File Link(Might not be accessible for non-pro users):- https://app.powerbi.com/groups/me/reports/eaa0f9be-c1e5-464d-92f7-77dfa7012e08/ReportSectionc97c0d50b5e5eab04bb3

# Why ADF?

Before starting Let me explain Why I've decided to Used ADF
Since ADF provides a vast no. of connectors that supports all our Data Integration & Orchestration.
It has a vast array of Connectors that can be used to improve the project further in future.
It is suitable for Ingestion, Transformation & Publish.
The Project Can be divide into 5 major parts for better understanding.

**1. Ingestion of Raw Data:-**
In this project, I've created parametrized linked Services that helps in ingesting data through various Websites using the HTTP Connectors which are all ingested into a data lake Gen2 Storage account.

**2. Transform/Analyze:-**
By creating Different Data Flows for transforming various kinds of Data.
I've used HDInsight for one of the Datasets & Azure Data bricks for another one. Here ADF is used for orchestration during transformation.
The difference in all the above 3 is that Data Flow gives us a code-free Transmission tool, which makes it easy to develop and maintain.
While it is not suitable for more complex transformations, for which we use Azure HD insights, & Azure Data Bricks which requires us to write scripts in Python, Scala - Spark supported & Hive & Pig for HDInsights.

**3. Storage & visualization:-**
The following data is then Pushed to an Azure SQL Database Server named coronavirus19- server which contains the Database covid-DB. Azure Synapse analytics(formerly Azure Data Warehouse) is much better for large Data warehouses for utilizing** Azure's Massive Parallel Processing (MPP)Architecture **but since our Data is very small Azure SQL can do the job pretty easily.
For storage, I've Used Azure Data Lake Gen 2 time & again. It is Azure's recommended storage solution for building enterprise-level databases, It can store Multiple petabytes of data while sustaining hundreds of Gbs of throughput. Azure Data Lakes is a Hierarchical Storage solution that can store unstructured data hierarchically. 
**ADLS is famous for its 3V's** which are

<ol>  a. Volume <br>
  b. Velocity <br>
  c. and Variety <br></ol>
It is built on azure blob storage but with the benefits of performance management & security.
This Data is then used for creating a PowerBI Report for Reporting Trends.

**4. Functioning:-**
**a. The Pipelines:-**
The Functioning of the project are controlled by the various pipelines created by us for
 <ol> 1. Ingesting Data <br>
2. Processing Data <br>
3. Adding processed Data to Azure SQL Database. <br>
4. Sequentially connecting all the pipelines for execution in a nested pipeline named pl_execute_. <br></ol>

**b. The Triggers**
Tumbler Window triggers are used to automate the working of the pipelines the Trigger is set to work at 12:00 A.M. IST Midnight at a frequency of 24 Hours. After which all the pipelines run sequentially starting with ingesting Raw Data from various websites.

**c. Linked Service**
A linked Service is like a connection string that is used to establish a connection between data factory and external data sources. It contains information regarding establishing a secure connection.

**5. Monitoring:-**
We can Monitor all the Pipeline runs & Trigger run in the Monitor tab of the Azure Data Factory which will let us know if there has been an error occurred during their execution.

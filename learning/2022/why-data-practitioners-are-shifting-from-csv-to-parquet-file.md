# Why Data Practitioners are Shifting from CSV to Parquet File

Chances are that you know what a CSV file is. It is widely used by data scientists, data engineers, and data analysts. But CSV files have some innate limitations. For one, they are relatively slow and not as efficient for data processing. Data scientists today are now shifting away from CSV files to using a better alternative - Parquet files.

In this article, we will discuss what a Parquet file is, its advantages over CSV files, and how to get started with it.

## What is a Parquet File?

Parquet is a column-oriented file storage format. By column-oriented, we mean the data is stored and accessed column by column. Parquet files utilize the record shredding and assembly model [designed by Google](https://research.google/pubs/pub36632/) for better performance. This design efficiently handles the storage and retrieval of big data.

If for instance, you wish to query a subset of data, Parquet files identify the columns you wish to query without parsing the entire rows. A CSV file, on the other hand, which is row-oriented, checks every row before the output is presented, causing the querying time to be longer. 

Here are some properties of parquet files

1.  It is column-oriented.
    
2.  It is an efficient file compression scheme.
    
3.  It automatically stores file schema and metadata.
    
4.  It works well for big data with complex data structures.
    

## Advantages of Parquet over CSV

### 1. Better compression
    

Parquet files have a smaller file than CSV files due to their excellent compression. This means that you save some cost for data storage compared to having the same data in a CSV format. Let’s do some practical experiments to prove this. We would compare the file size of the same data in both CSV and Parquet formats.

To do this, I downloaded a [dataset from Kaggle](https://www.kaggle.com/datasets/thedevastator/adoptable-dogs-in-the-us?resource=download) and loaded it into a Jupyter notebook using pandas.

```
from time import time  
import os  
import numpy as np  
import pandas as pd  
df_csv = pd.read_csv("allDogDescriptions.csv")
```
  

Next, we converted the file to parquet format using the to_parquet() method and imported it into the Jupyter notebook.

```
df_csv.to_parquet("allDogDescriptions.parquet")  
df_parquet = pd.read_parquet("allDogDescriptions.parquet")
```
  

Now, let’s check the file size of both files.
```
os.path.getsize("allDogDescriptions.csv")  
os.path.getsize("allDogDescriptions.parquet")
```

![](https://lh4.googleusercontent.com/2NIdei-1yMs5xysH1sIzM8Ioi8jmyV7is8xhUOMmH2AvBfsbWUWfurdr2ZxQKQ75-CSls-Y-ZX_4nhTHpcWUeLKu3RG6IdkSS4ltTpCZ6PfHxar6dzJ008MX96EJPWhTj49UGwbWMHcKV4DJUJvnPVPArZoiq024fxQ5ookG93pPd-J3EKch7-YmR3lyxw)

As seen, the CSV file has a file size of 67.3 MB while the Parquet file has a file size of 25.9 MB. That is a 2.6X more compression for the Parquet file.

### 2. Faster read queries
    

Because the Parquet format is column-oriented, it has a faster read time than CSV files. To continue our experiment, let’s check how long it takes to read both files.

```
%time df_csv = pd.read_csv("allDogDescriptions.csv")  
%time df_parquet = pd.read_parquet("allDogDescriptions.parquet")
```
  

The result?

![](https://lh5.googleusercontent.com/6dAMmgWiJSAXylMmKqUIJTtCg6vsZv0dU7Y3r6soBZyVFIwu_JeYkdGDl4_cuasidin-T0Nk8jXb41fwxNLs4EUJJ3Z5FV9XfVBjEjvcMfLXTlF0AQ2Qi5eaSm0vqSva_r00Wnw2DlappwAKy1oO1WbxcvgE9nbSmLlSquAm-Ke42cHcRwleT90t7vRn7Q)

The CSV file took 757 milliseconds whereas the Parquet file took 277 milliseconds. This means the Parquet file was read 2.7X faster than the CSV file.

### 3. Uses column pruning for optimization
    

Parquet file uses column pruning to drop columns that are not used. This leads to lower I/O in subsequent operations and better storage optimization. For example, if you have a large dataset with 200 columns but you only need 10 for your analysis, you can set the parquet file to only read the columns you need when importing the file. This is possible, again because of the column-oriented format for storing data in the Parquet file.

To achieve this on a CSV file, the entire will first be read then the required column will be filtered. The higher I/O in this case leads to longer query time eventually. Let’s get to our experiment again. 

The dataset has 36 columns but if we only wish to work with two columns, say "breed_primary", "breed_secondary". We can check how long it takes to impor both file formats. For the CSV file, we import the dataset and pass the "usecol" argument.

```
%time pd.read_csv("allDogDescriptions.csv", usecols=["breed_primary", "breed_secondary"])
```
  

![](https://lh5.googleusercontent.com/zeqRXsIMp-odwFRkMpwokv4qodSg2zacasoQq3W4TnxGLs4uNHt_b1CxPeUXsLrT93WzWeKw5Yf6apuj2VHD63QV5tB4mOe1S1EU-1duF0f0-FcRMxMGszXmqIXybJGf7GcJGVPih8VEIfnJ4yWhbRobgXapkCUc7h7ZwdSN6oNZR4__JzaZJsOoosHO1A)

Notice, it took 344 milliseconds. 

Now, let's perform the same operation for the Parquet file.

```
%time pd.read_parquet("allDogDescriptions.parquet", columns = ["breed_primary", "breed_secondary"])
```
  

![](https://lh4.googleusercontent.com/cWkO2232J3ZidZCksy9v2nkugzWBffW-7SqNnuaGKybPXL6XfSjdr-TkW1egc_buuzx8qC-mFWYD3nrIH6Mr2jGUW-xwsdmdqw5rX-etVQ6UyDQbzbGDhULm3f5xtOp7TNJRqmQkinq5gsFv3Y_4XPF7TIUskx5tYyezzLz_ugjWryY3xY6NdLdM8IKGrw)

The same operation took 50.7 milliseconds. It means the Parquet file was 6X faster than its CSV counterpart.

The table below summarizes the comparison between a CSV file and a Parque file.
  

| Operation               | CSV File | Parquet File | Parquet/CSV ratio      |
|-------------------------|----------|--------------|------------------------|
| Storing data            | 67.4 MB  | 25.9 MB      | Parquet is 2.6X faster |
| Reading the dataset     | 757 ms   | 277 ms       | Parquet is 2.7X faster |
| Importing a data subset | 344 ms   | 50.7 ms      | Parquet is 6X faster   |

Other advantages of parquet format over CSV format include:

### 4. Parquet files store schema info and metadata automatically
    

A parquet file stores the column names and the data types in each column without you explicitly specifying it. 

### 5. Parquet files do predicate pushdown filtering
    

This implies that the amount of data read from the source can be reduced based on your query. 

If for instance, you wish to filter values in a column greater than 20. Parquet creates a subgroup of rows and determines the min and max for each group. To interpret your query, Parquet reads only groups where the max value is greater than 20. It completely neglects row groups where the max value is less than 20. The end result is a faster and most efficient query.

### 6. Immutability
    

Parquet data cannot be changed which is as advantageous. Immutable data means consistency and homogeneity across the board. Rather than changing the data, the query of code should be changed.

## Why is it Important for Data Practitioners?

Imagine you are a data engineer that does a lot of queries on Amazon AWS. It is not just enough to query data and manage databases. The onus is on you to do it as efficiently as possible and save costs.

Parquet files help you store data efficiently by compressing the data into a smaller file size. Meaning you pay less for the Amazon S3 instance or any other web service you stored the data on. Furthermore, you can save money on queries with Parquet files. Query services such as Apache Hive or Amazon Athena charges based on the size of data parsed in a query. Since Parquet’s file column-based orientation ensures only relevant columns are parsed, you get to save money by using only the data you need and not the entire dataset. 

In addition, Parquet files have a faster query time. Thus, if your web service charges based on compute (which most of them do), you save extra money by using less compute with Parquet files. 

  

## How to Get Started with Parquet File

In the experiment we performed, getting started with Parquet is as good as converting the CSV file with a parquet file in pandas. But Parquet is also acceptable in Spark, Dask, BigQuery, and so on.  To use parquet in Spark, you can simply write a Spart dataframe to a Parquet file format. The same thing applies to Dask. Writing the CSV file to a Parquet file gets you up and running with Parquet files on Dask. To use it on BigQuery, simply load the file as a parquet file from Google Cloud Storage.

  

## Wrapping up

In this article, we have discussed why there is a gradual shift from the ubiquitous CSV file format to a less popular format - Parquet. The advantages of Parquet files are undoubtedly surreal, beating CSV files in critical metrics such as data storage, query time, and compute. With these gains, the Parquet file format is well on its way to overtaking CSV files in popularity. You know how to get started with it.

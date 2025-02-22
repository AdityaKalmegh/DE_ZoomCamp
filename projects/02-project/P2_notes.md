## Amazon Datasets

https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/W96OFO 
These datasets consist of product reviews we ourselves collected from Amazon.com, starting from the year 2008 to 2020, spanning across seven different domains, namely, book (Becoming by Michelle Obama), pharmaceutical (Turmeric Curcumin Supplement by Natures Nutrition), electronics (Echo Dot 3rd Gen by Amazon), grocery (Sparkling Ice Blue Variety Pack), healthcare (EnerPlex 3-Ply Re-usable Face Mask), entertainment (Harry Potter: The Complete 8-Film Collection), and personal care (Nautica Voyage By Nautica). These datasets consist of 5000 reviews each.

https://registry.opendata.aws/amazon-berkeley-objects/ 
Amazon Berkeley Objects (ABO) is a collection of 147,702 product listings with multilingual metadata and 398,212 unique catalog images. 8,222 listings come with turntable photography (also referred as "spin" or "360º-View" images), as sequences of 24 or 72 images, for a total of 586,584 images in 8,209 unique sequences. For 7,953 products, the collection also provides high-quality 3d models, as glTF 2.0 files.


https://amazon-reviews-2023.github.io/
    Larger Dataset: We collected 571.54M reviews, 245.2% larger than the last version;
    Newer Interactions: Current interactions range from May. 1996 to Sep. 2023;
    Richer Metadata: More descriptive features in item metadata;
    Fine-grained Timestamp: Interaction timestamp at the second or finer level;
    Cleaner Processing: Cleaner item metadata than previous versions;
    Standard Splitting: Standard data splits to encourage RecSys benchmarking.

## Steps 

# 1. Describe dataset, define problem statement - 
    Selecting a dataset of interest (see Datasets)
    Creating a pipeline for processing this dataset and putting it to a datalake
    Creating a pipeline for moving the data from the lake to a data warehouse
    Transforming the data in the data warehouse: prepare it for the dashboard
    Building a dashboard to visualize the data

# 2.The pipeline could be stream or batch: this is the first thing you'll need to decide

    Stream: If you want to consume data in real-time and put them to data lake
    Batch: If you want to run things periodically (e.g. hourly/daily)

# 3. You don't have to limit yourself to technologies covered in the course. You can use alternatives as well:

    Cloud: AWS, GCP, Azure, ...
    Infrastructure as code (IaC): Terraform, Pulumi, Cloud Formation, ...
    Workflow orchestration: Airflow, Prefect, Luigi, ...
    Data Warehouse: BigQuery, Snowflake, Redshift, ...
    Batch processing: Spark, Flink, AWS Batch, ...
    Stream processing: Kafka, Pulsar, Kinesis, ...

# 4. 
    Problem description
        0 points: Problem is not described
        2 points: Problem is described but shortly or not clearly
        4 points: Problem is well described and it's clear what the problem the project solves
    Cloud
        0 points: Cloud is not used, things run only locally
        2 points: The project is developed in the cloud
        4 points: The project is developed in the cloud and IaC tools are used
    Data ingestion (choose either batch or stream)
        Batch / Workflow orchestration
            0 points: No workflow orchestration
            2 points: Partial workflow orchestration: some steps are orchestrated, some run manually
            4 points: End-to-end pipeline: multiple steps in the DAG, uploading data to data lake
        Stream
            0 points: No streaming system (like Kafka, Pulsar, etc)
            2 points: A simple pipeline with one consumer and one producer
            4 points: Using consumer/producers and streaming technologies (like Kafka streaming, Spark streaming, Flink, etc)
    Data warehouse
        0 points: No DWH is used
        2 points: Tables are created in DWH, but not optimized
        4 points: Tables are partitioned and clustered in a way that makes sense for the upstream queries (with explanation)
    Transformations (dbt, spark, etc)
        0 points: No tranformations
        2 points: Simple SQL transformation (no dbt or similar tools)
        4 points: Tranformations are defined with dbt, Spark or similar technologies
    Dashboard
        0 points: No dashboard
        2 points: A dashboard with 1 tile
        4 points: A dashboard with 2 tiles
    Reproducibility
        0 points: No instructions how to run the code at all
        2 points: Some instructions are there, but they are not complete
        4 points: Instructions are clear, it's easy to run the code, and the code works

# 5. 

implementing following could significantly enhance the quality of your project:

    Add tests
    Use make
    Add CI/CD pipeline

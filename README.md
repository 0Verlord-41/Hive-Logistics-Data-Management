# Hive-Logistics-Data-Management

Logistics data management using Hadoop Hive Warehouse in GCP Dataproc and Airflow to orchestrate and run the tasks in a scheduled manner.

- Airflow DAG have total 6 tasks.
- A GCP objects sensor operator from Airflow keeps tarck of new files being uploaded in the source bucket.
- Tables inside Hive are created using submit hive job operator.
- Inside Hive a database is created, then an external table is created in hive that uses the files from source bucket to load the data.
- There is a partitioned table based on date which loads the data from External table.
- Make sure to set these hive properties for dynamic partition.
```
SET hive.exec.dynamic.partition = true;
SET hive.exec.dynamic.partition.mode = nonstrict;
```
- Finally source file is moved from the source bucket to the archive bucket.

# Architercture

- Dataproc cluster (For Hadoop and Spark workloads)
- Composer (Airflow)
- Storage Bucket

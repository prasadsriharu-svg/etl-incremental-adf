# Incremental ETL Migration with Azure Data Factory

This project demonstrates how to build an **incremental load pipeline** using **Azure Data Factory (ADF)** and **Azure Data Lake Storage Gen2 (ADLS)**.

## 🚀 Features
- **Linked Services**: Connect to SQL Server and ADLS Gen2
- **Datasets**: Define source (SQL table) and sink (ADLS CSV)
- **Pipeline**: Copy activity with watermark parameter for incremental loading
- **Secure Access**: Service principal authentication for ADLS

## 🛠️ Setup
1. Create linked services for SQL Server and ADLS.
2. Define datasets for source and sink.
3. Deploy the pipeline JSON in ADF.
4. Pass `WatermarkValue` parameter (e.g., last run timestamp).
5. Run pipeline → only new/updated records are copied.

## 📊 Example
```sql
SELECT * FROM <_table_name> WHERE LastModifiedDate > @pipeline().parameters.WatermarkValue

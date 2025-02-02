## Data Engineering Interview Questions

### 1. What is the difference between Copy Activity and Data Flow in ADF?
- **Copy Activity:** Used to transfer data between data stores without transformation.
- **Data Flow Activity:** Used when data transformations are required before moving data.

### 2. How do you monitor and troubleshoot pipelines in ADF?
- Use the **Monitor** tab in ADF.
- Check pipeline status, errors, and logs.
- Debug the pipeline before execution.
- Validate linked service authentication and connections.

### 3. Implementing a pipeline for:
- **Ingesting files from ADLS Gen2.**
- **Applying transformations.**
- **Loading into SQL Database.**

**Solution:**
- Create necessary resources (ADLS Gen2, SQL Database, ADF).
- Establish **Linked Services** for ADLS Gen2 and SQL Database.
- Design pipeline with **Data Flow Activity** for transformations.
- Configure source (ADLS Gen2) and sink (SQL Database).
- Debug, validate, and execute.

### 4. What is Integration Runtime in ADF?
- **Azure IR:** Cloud-based data movement & transformation.
- **Self-hosted IR:** Connects on-premise/private network data sources to Azure.
- **Azure-SSIS IR:** Runs SSIS packages in Azure.

### 5. Handling Schema Drift in ADF
- Enable **Schema Drift** in Data Flow Activity.
- Set up **Monitor Alerts** for schema changes.
- Ensure flexible column mappings.

---

## Azure Databricks

### 1. Explain Delta Lake
- **Storage layer** on ADLS & cloud data lakes.
- Supports **ACID Transactions, Schema Evolution, Time Travel, and Merge Operations**.

### 2. Optimizing Spark Jobs in Databricks
- **Select relevant columns**
- **Repartition data**
- **Cache frequently used data**
- **Use Broadcast Joins**
- **Tune Spark configurations**

### 3. DataFrame vs RDD in PySpark
- **RDD:** Immutable, low-level API, manual transformations.
- **DataFrame:** Structured, supports SQL queries, optimized execution.

### 4. Databricks & ADF Integration
- Create **Linked Services** in ADF.
- Use **Databricks Notebook Activity**.
- Set up transformations in Databricks Notebooks.

### 5. MLflow in Databricks
- **Experiment Tracking**
- **Model Management**
- **Reproducibility**

---

## PySpark

### 1. Handling Large Datasets
- **Distributed processing**
- **Lazy evaluation**
- **Catalyst Optimizer**
- **Parallelism**

### 2. Removing Duplicates
```python
df.dropDuplicates(["column_name"]).show()
```

### 3. Broadcast Variables
```python
from pyspark.sql.functions import broadcast
df1.join(broadcast(df2), on='key', how='inner')
```

### 4. Catalyst Optimizer
- Optimizes execution plans for **fast processing**.

### 5. Handling Skewed Data
- **Repartitioning**
- **Coalesce**

---

## SQL

### 1. Second-Highest Salary
```sql
SELECT MAX(salary) AS SecondHighest FROM Employee WHERE salary < (SELECT MAX(salary) FROM Employee);
```

### 2. Optimizing SQL Queries
- **Indexing**
- **Partitioning**
- **Query Optimization**

### 3. Window Functions
- Used for **ranking, running totals, moving averages**.

### 4. Finding Duplicate Rows
```sql
SELECT column1, COUNT(*) FROM table_name GROUP BY column1 HAVING COUNT(*) > 1;
```

### 5. SQL Indexing
- Improves query performance by **reducing scan time**.

---

## Azure Storage

### 1. Securing Azure Data Lake with Key Vault
- Store and retrieve **secrets & keys** securely.
- Use **Managed Identity for Authentication**.

### 2. Blob Storage vs ADLS Gen2
| Feature | Blob Storage | ADLS Gen2 |
|---------|-------------|-----------|
| Storage Type | Unstructured | Structured & Unstructured |
| Hierarchical Namespace | No | Yes |
| Performance | Moderate | High |
| Security | RBAC | ACLs & RBAC |

### 3. Configuring Storage for ADF
- **Create Storage Account**
- **Generate SAS Token or Use Managed Identity**
- **Create Linked Service in ADF**
- **Configure Dataset & Pipeline**

---

## General Data Engineering

### 1. Managing Data Pipeline Errors
- Implement **Retry Logic**.
- Use **Monitoring & Logging**.

### 2. Migrating On-Premise Data to Azure using ADF
- Set up **Self-hosted Integration Runtime**.
- **Copy Data Activity** to transfer data securely.

### 3. Best Practices for Databricks Pipelines
- **Modular Code**
- **Cluster Auto-Scaling**
- **Efficient Data Partitioning**

### 4. Monitoring Data Pipeline Performance
- **Use ADF Monitor Tab**.
- **Enable Logging in Databricks**.
- **Set up Alerts & Notifications**.

---

## Practical Use Case

### Copying CSV from Blob Storage to SQL using ADF
1. **Create Azure Resources**
2. **Set Up Linked Services** (Blob Storage, SQL Database)
3. **Create Datasets**
4. **Build ADF Pipeline**
5. **Use Copy Data Activity** (Source: Blob, Sink: SQL)
6. **Debug, Validate, and Monitor Execution**


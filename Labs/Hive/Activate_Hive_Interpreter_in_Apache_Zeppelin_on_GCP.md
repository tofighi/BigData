# Activating Hive Interpreter in Apache Zeppelin (GCP Dataproc - 2.3.18-ubuntu22)

This guide explains how to activate and configure the **Hive interpreter** in an **Apache Zeppelin** notebook running on **Google Cloud Platform (GCP) Dataproc** with **2.3.18-ubuntu22** version of image.

---

## Assumptions and Prerequisites

This guide assumes Apache Zeppelin and Hive are running on **GCP Dataproc**.

### Assumptions

- A Dataproc cluster is already created
- Hive and HiveServer2 are installed via Dataproc
- Zeppelin is installed on the cluster (or via initialization actions)
- Required firewall rules allow access to the Zeppelin UI

### Prerequisites

- **Standard Dataproc Image 2.3 (Ubuntu 22 LTS, Hadoop 3.3, Spark 3.5)** -
First released on 06/09/2025

---

## Steps to Activate Hive Interpreter

### 1. Open the Interpreter Settings

1. Open Zeppelin in your browser
2. Navigate to **Interpreters** from the top menu
3. Click **Create** to add a new interpreter

---

### 2. Configure Interpreter Properties

Set the following properties exactly as shown:

#### Hive Connection URL

**default.url**: 
```text
jdbc:hive2://localhost:10000
```

#### Username and Password

- Leave **username** empty
- Leave **password** empty

#### Hive JDBC Driver

**default.driver:**
```text
org.apache.hive.jdbc.HiveDriver
```

---

### 3. Add Dependencies

Under the **Dependencies** tab, add the following artifacts:

```text
org.apache.hive:hive-jdbc:3.1.3
org.apache.hadoop:hadoop-common:3.3.6
```

Ensure both dependencies are added before saving the interpreter.

---

### 4. Save and Restart Interpreter

1. Click **Save**
2. Restart the interpreter if prompted

After restarting, the Hive interpreter should be available in Zeppelin notebooks.

---

## Using Hive in a Zeppelin Notebook

Create or open a Zeppelin notebook and use the Hive interpreter (usually `%hive`) to execute Hive queries.

Example:

```sql
%hive
SHOW DATABASES;
```

---

## Video Tutorial

For a visual walkthrough and additional explanation, watch the following video:

[Activate Hive Interpreter in Zeppelin](https://youtu.be/lNkUOf6BlPA)


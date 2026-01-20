# Activate Hive Interpreter in Apache Zeppelin (GCP Dataproc)

This guide explains how to activate and configure the **Hive interpreter** in an **Apache Zeppelin** notebook running on **Google Cloud Platform (GCP) Dataproc**.

---

## Assumptions and Prerequisites

This guide assumes Apache Zeppelin and Hive are running on **GCP Dataproc**.

### Assumptions

- A Dataproc cluster is already created
- Hive and HiveServer2 are installed via Dataproc
- Zeppelin is installed on the cluster (or via initialization actions)
- Required firewall rules allow access to the Zeppelin UI

### Prerequisites

- Apache Zeppelin is running on the Dataproc cluster
- HiveServer2 is running and listening on port `10000`
- You have access to the Dataproc master node

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

```text
hive.url=jdbc:hive2://localhost:10000
```

> 💡 **Dataproc Note:**  
> If Zeppelin is not running on the Dataproc master node, replace `localhost` with the **Dataproc master internal hostname**.

#### Username and Password

- Leave **username** empty
- Leave **password** empty

#### Hive JDBC Driver

```text
hive.driver=org.apache.hive.jdbc.HiveDriver
```

---

### 3. Add Dependencies

Under the **Dependencies** tab, add the following artifacts:

```text
org.apache.hive:hive-jdbc:0.14.0
org.apache.hadoop:hadoop-common:2.6.0
```

Ensure both dependencies are added before saving the interpreter.

---

### 4. Save and Restart Interpreter

1. Click **Save**
2. Restart the interpreter when prompted

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

[![Activate Hive Interpreter in Zeppelin](https://img.youtube.com/vi/4qRbDcXY6YA/0.jpg)](https://www.youtube.com/watch?v=4qRbDcXY6YA)



## Reference

- Video tutorial: https://www.youtube.com/watch?v=4qRbDcXY6YA
- Configuration and code examples are demonstrated in the video

---

✅ You have successfully activated the Hive interpreter in Apache Zeppelin on GCP Dataproc.

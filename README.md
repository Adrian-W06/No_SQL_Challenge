# Eat Safe, Love — NoSQL Food Establishment Analysis

This project demonstrates how to import, set up, and analyze a NoSQL dataset using **MongoDB** and **Python** in Jupyter Notebooks. The dataset contains information on food establishments in the UK.

---

## 📂 Files

- `NoSQL_setup_starter.ipynb`: Prepares the MongoDB environment and imports the dataset.
- `NoSQL_analysis_starter.ipynb`: Analyzes the data using Python and MongoDB queries.

---

## 🚀 Instructions

### 📌 Part 1: Setup (`NoSQL_setup_starter.ipynb`)

#### 🔹 Step 1: Import Data into MongoDB

From the terminal, import the JSON data file into MongoDB:

```bash
mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json
```

- `uk_food`: Name of the database.
- `establishments`: Name of the collection.
- `--drop`: Clears any existing data in the collection before import.

#### 🔹 Step 2: Establish a Connection

```python
from pymongo import MongoClient
import pandas as pd
from pprint import pprint

# Connect to MongoDB
client = MongoClient()
db = client['uk_food']
collection = db['establishments']
```

This connects your Jupyter Notebook to the local MongoDB server and sets up references to the target database and collection.

---

### 📊 Part 2: Analysis (`NoSQL_analysis_starter.ipynb`)

#### 🔹 Step 1: Initial Setup

```python
from pymongo import MongoClient
import pandas as pd
from pprint import pprint
```

This imports necessary libraries:
- `pymongo` to interact with MongoDB,
- `pandas` for data manipulation,
- `pprint` for readable output.

#### 🔹 Step 2: Connect to the MongoDB Collection

```python
client = MongoClient()
db = client['uk_food']
collection = db['establishments']
```

Ensures access to the database for running queries.

#### 🔹 Step 3: Filtering Using MongoDB Queries

Examples might include:
- Filtering for establishments with specific hygiene scores.
- Searching for establishments in a particular region.
- Matching establishments that require improvement.

Example:

```python
query = {"scores.Hygiene": {"$lt": 5}}
results = list(collection.find(query))
```

#### 🔹 Step 4: Convert to DataFrame for Analysis

```python
df = pd.DataFrame(results)
df.head()
```

This step brings the MongoDB query results into pandas for deeper analysis or visualization.

---

## ✅ Requirements

- Python (3.x)
- Jupyter Notebook
- MongoDB (local or cloud instance)
- `pymongo`
- `pandas`

Install required Python packages:

```bash
pip install pymongo pandas
```

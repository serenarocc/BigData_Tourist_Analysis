# TourismPolito Data Analysis Project

TourismPolito is an international company that tracks tourists as they visit points of interest (POIs) worldwide. 
Statistics about tourists and POIs are computed from the following input data files collected over the last thirty years.

---

## Input Data Files

### 1. Tourists.txt
Contains information about the tourists managed by TourismPolito.
- **Scale:** Over 300,000,000 records.
- **Format:** `CodT,Name,Surname,City,Country`
- **Description:** `CodT` is the unique identifier, `Name`/`Surname` are personal details, `City`/`Country` represent the residence.
- **Example:** `T10,Mario,Rossi,Carmagnola,Italy`

### 2. POIs.txt
Contains information about the points of interest (POIs) worldwide.
- **Scale:** Over 400,000,000 records.
- **Format:** `POIID,name,category,latitude,longitude,POICountry`
- **Description:** `POIID` is the unique identifier, `latitude`/`longitude` are geolocations, and `POICountry` is the country.
- **Example:** `POI23,Egyptian Museum,Museum,45.0684433,7.6844128,Italy`

### 3. Visits.txt
Contains information about who visited each POI and when.
- **Scale:** Over 1,000,000,000 records.
- **Format:** `CodT,StartTimestamp,POIID,Duration`
- **Description:** `StartTimestamp` follows `YYYY/MM/DD-HH:MM`. `Duration` is in minutes. 
- **Key Note:** The combination `(CodT, StartTimestamp)` is the primary key.
- **Example:** `U10,2022/11/07-21:40,POI23,48.5`

---

## Task Requirements

### Part 1: Tourist(s) with the most visits to Italian POIs
Select all tourists associated with the **maximum number of visits** to POIs located in Italy.
- **Output Folder:** First HDFS output folder.
- **Format:** `CodT` (one per line).

### Part 2: Number of distinct visited categories in 2024 (Italy)
For **each tourist**, count the number of **distinct** POI categories visited in 2024, considering only POIs located in Italy.
- **Important:** If a tourist never visited an Italian POI in 2024, the output must be `0`.
- **Output Folder:** Second HDFS output folder.
- **Format:** `CodT, NumberOfDistinctCategories`

---

## Example (Part 2)

**Setup:**
- **Tourists:** T1, T2, T3.
- **Italian POIs:** - POI1 (Museum), POI2 (Museum), POI3 (Restaurant), POI4 (Railway station), POI5 (Hotel).

**Activity in 2024:**
1. **T1** visited POI1, POI2, POI3 → Categories: *Museum, Museum, Restaurant* → **2 Distinct**.
2. **T2** visited POI1, POI4 → Categories: *Museum, Railway station* → **2 Distinct**.
3. **T3** visited nothing in Italy → **0 Distinct**.

**Expected Output:**
```text
T1,2
T2,2
T3,0


---

## Tech Stack

Apache Spark & PySpark running on HDFS infrastructure.
Methodology: Leveraged Spark RDDs

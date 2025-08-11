# socrata_metadata_updates

# Dataset Metadata Updater for Maryland Open Data Portal

## Overview

This Python script automates updating metadata for datasets hosted on the Maryland Open Data Portal (`opendata.maryland.gov`). It reads dataset information from a CSV file and updates metadata fields such as:

- **Attribution Link** (from the CSV column `ersi_link`)
- **Custom fields** including:
  - `Jurisdiction`
  - `Agency`
  - `Time Period` details (Update Frequency, Date Metadata Written, Time Period of Content)
  - `Place Keywords`
  - `Tags`
- **Description** by appending the attribution link sentence to the existing description

The script authenticates using provided credentials and makes GET and PUT requests to the portal's API to retrieve and update dataset metadata.

---

## Prerequisites

- Python 3.x
- Python packages:
  - `pandas`
  - `requests`
- A CSV file named `ersi_final.csv` with columns including:
  - `uid` (dataset ID)
  - `ersi_link` (URL for attribution link)
  - `create_date` (used for time period metadata)
- A `secret_data.py` file containing your API username and password as:
  ```python
  userpass = ("your_username", "your_password")

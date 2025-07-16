---
layout: single
title: "Downloading ERA5 Atmospheric Reanalysis"
date: 2025-07-08
tags: [atmospheric-data]
author_profile: true
excerpt: "We use the Climate Data Store (CDS) to download daily wind vectors from ERA5, which will later be used to construct atmospheric indices."
---

To begin, make sure you have:

- A registered account with the [Climate Data Store (CDS)](https://cds.climate.copernicus.eu/)
- cdsapi installed by following the [CDSAPI setup](https://cds.climate.copernicus.eu/how-to-api)
- Python 3 installed

Because we want to download multiple years of daily-resolution wind data, we’ll use the CDS API.

---

### Step 1: Configure Your Data Request

Go to the dataset **ERA5 hourly data on single levels from 1940 to present** and fill in the following options:

- **Product Type:** Reanalysis  
- **Variables:**  
  - `10m_u_component_of_wind`  
  - `10m_v_component_of_wind`
- **Years:** Start with `1979` (full loop through 2025 shown below)
- **Months and Days:** Select *all* 
- **Hours** `12:00`  -- most representative for the day 
- **Geographical Boundaries:**  
  - North: `-50`  
  - West: `-180`  
  - South: `-90`  
  - East: `180`  
  *(Covers the Southern Ocean)*
- **Data Format:** `NetCDF4 (experimental)`

At the bottom of the CDS interface, click **"Show API request"** and copy the generated Python code.

---

### Step 2: Use the CDS API with a Loop for Multiple Years

Below is an example script using the CDS API to download data from 1979 to 2024.

```python
import cdsapi
from datetime import datetime, timedelta
from concurrent.futures import ThreadPoolExecutor
import os

# Function to download ERA5 data for a specific day
def download_day(date_str):
    client = cdsapi.Client()

    year = date_str[:4] # breaking up the string
    month = date_str[4:6]
    day = date_str[6:8]

    # Define the folder and filename
    output_dir = os.path.join("data", year)  # e.g., data/1985
    os.makedirs(output_dir, exist_ok=True)   # Create folder if it doesn't exist

    filename = os.path.join(output_dir, f"era5_wind_{date_str}_12UTC.nc")

    print(f"→ Downloading {filename}")

    # Submit request to CDS API
    client.retrieve(
        "reanalysis-era5-single-levels",
        {
            "product_type": "reanalysis",
            "variable": ["10m_u_component_of_wind", "10m_v_component_of_wind"],
            "year": year,
            "month": month,
            "day": day,
            "time": ["12:00"],
            "data_format": "netcdf",
            "area": [-50, -180, -90, 180]
        },
        filename
    )

    print(f"  ✔ Done: {filename}")

# Generate list of all days from Jan 1, 1979 to Dec 31, 2024
start_date = datetime(1979, 1, 1)
end_date = datetime(2024, 12, 31)

date_list = []
current_date = start_date
while current_date <= end_date:
    date_list.append(current_date.strftime("%Y%m%d"))
    current_date += timedelta(days=1)

# Use a thread pool to download in parallel (adjust max_workers if needed)
with ThreadPoolExecutor(max_workers=4) as executor:
    executor.map(download_day, date_list)

```
### Step 3: Running the Script as a Batch Job or in the Background

Because we are downloading about 394,200 time steps (24hrx365dx45yr) it can take a while. In order to avoid potential interruptions we can run the script in the background. In my case, I will submit it as a job on a cluster. 

My python file is saved as `UV_Winds_1979-2025.py`, and I will run it using `nohup`: 

```
nohup python UV_Winds_1979-2025.py > UV_download.log 2>&1 &
```

This will keep it running in the background and you can check the progress/errors on `UV_download.log`

I recommend running:

```
tail -f UV_download.log 
```
...to check that it is running without any errors :)






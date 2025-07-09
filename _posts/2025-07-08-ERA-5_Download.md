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
- **Months, Days, and Hours:** Select *all*
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
client = cdsapi.Client()

dataset = "reanalysis-era5-single-levels"
request = {
    "product_type": ["reanalysis"],
    "variable": [
        "10m_u_component_of_wind",
        "10m_v_component_of_wind"
    ],
    "year": ["1979"],
    "month": [
        "01", "02", "03",
        "04", "05", "06",
        "07", "08", "09",
        "10", "11", "12"
    ],
    "day": [
        "01", "02", "03",
        "04", "05", "06",
        "07", "08", "09",
        "10", "11", "12",
        "13", "14", "15",
        "16", "17", "18",
        "19", "20", "21",
        "22", "23", "24",
        "25", "26", "27",
        "28", "29", "30",
        "31"
    ],
    "time": [
        "00:00", "01:00", "02:00",
        "03:00", "04:00", "05:00",
        "06:00", "07:00", "08:00",
        "09:00", "10:00", "11:00",
        "12:00", "13:00", "14:00",
        "15:00", "16:00", "17:00",
        "18:00", "19:00", "20:00",
        "21:00", "22:00", "23:00"
    ],
    "data_format": "netcdf",
    "download_format": "unarchived",
    "area": [-50, -180, -90, 180]
}
## Here we just copy from below and add a for loop for each year:

for year in range(1979, 2025):
    req = request.copy()
    req["year"] = [str(year)] 

    out_fname = f"era5_10m_wind_{year}.nc"
    print(f"→ requesting {year}, saving to {out_fname}")
    client.retrieve(dataset, req, out_fname)
    print(f"  ✔ done {out_fname}")
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






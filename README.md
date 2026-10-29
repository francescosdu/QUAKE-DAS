# DAS Single Station Workflow

Workflow for detection and analysis of DAS data from individual virtual channels.
The workflow integrates:  
- **PhaseNet** (Zhu & Beroza 2018) for performing **phase picking**  
- **GaMMa** (Zhu et al. 2022) for performing **phase assocation**  
- **NLLoc** (Lomax et al. 2000) for determining **hypocentral location**  


## Requirements

We suggest using a python version >= 3.11. Install the Python dependencies with:

```bash
git clone https://github.com/francescosdu/QUAKE-DAS.git  
cd QUAKE-DAS  
pip install -r requirements.txt
```

## Notebooks

The **detection analysis** with PhaseNet is performed in:

`01_detection_analysis.ipynb`


This notebook integrates xdas (Trabattoni et al. 2025) for reading DAS data and extracting strain rate records from virtual receivers as Obspy streams, which are fed to pre-trained ML picker (Seisbench, Woollam et al. 2022). In this application, we employed the pretrained PhaseNet models on the original (Zhu & Beroza 2018) and DiTing (Zhao et al. 2023) datasets on a seismic event recorded by DAS within the Irpina Near-Fault Observatory (INFO). Phase picks are associated using GaMMA (Zhu et al. 2022), ruling out false declarations and retaining coherent phase arrivals. 

**Location analysis** with NLLoc is performed in:

`02_location_analysis.ipynb`


This notebook uss the arrival times obtained from the integration of PhaseNet and GaMMA and determines the hypocentral coordinates with NLLoc (Lomax et al. 2000) using an interpolated 1D velocity model for the Irpinia region. The final location and the resulting PDF is displayed against the reference hypocentral location from INFO, along with location uncertainties and quality metrics.

**NOTE**: Before proceeding with earthquake location, travel-time grids have to be computed using "generate_NLLoc_grid.sh". P and S travel-time grid requires ~90GB of storage


**Magnitude estimation** is performed in:

`03_local_magnitude.ipynb`


This notebook evaluates the local magnitude of the events converting strain rate records in displacement measurements (Trabattoni et al. 2023) and using a local magnitude scale for the Irpinia region (Bobbio et al. 2009). Local magnitude estimation and its uncertainty is compared against the value arising from the use of seismic stations from the conventional INFO network.

## Funding
This work is part of the TRANSFORM² project which aims to improve physical and digital infrastructure across Near-Fault Observatories (NFOs) in Europe.

TRANSFORM² is funded by the European Union under project number 101188365 within the HORIZON-INFRA-2024-DEV-01-01 call.

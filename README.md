# DAS Single Station Workflow

Workflow for detection and analysis of DAS data from individual virtual channels.
The workflow integrates:  
-PhaseNet (Zhu & Beroza 2018) for performing phase picking  
-GaMMa (Zhu et al. 2022) for performing phase assocation  
-NLLoc (Lomax et al. 2000) for determining hypocentral location  


## Requirements

Install the Python dependencies with:

```bash
pip install -r requirements.txt
```

## Notebook

The detection analysis with PhaseNet is performed in:

`01_detection_analysis.ipynb`

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/francescosdu/DAS_single_station_workflow/blob/main/01_detection_analysis.ipynb)

This notebook integrates xdas (Trabattoni et al. 2025) for reading DAS data and extracting strain rate records from virtual receivers as Obspy streams, which are fed to pre-trained ML picker (Seisbench, Woollam et al. 2022). In this application, we employed the pretrained PhaseNet models on the original (Zhu & Beroza 2018) and DiTing (Zhao et al. 2024) datasets on a seismic event recorded by DAS within the Irpina Near-Fault Observatory (INFO). Phase picks are associated using GaMMA (Zhu et al. 2022), ruling out false declarations and retaining coherent phase arrivals. 

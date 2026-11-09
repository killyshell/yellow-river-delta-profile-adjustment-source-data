# Yellow River Delta profile adjustment source data

Source data for **Small net bed level differences conceal contrasting profile adjustments in the Yellow River Delta**.

Authors: Nan Huang, Yonggui Yu, Gan Luo and Yi Zhang. Correspondence: Yi Zhang, yizhang@sdust.edu.cn.

Version: v1.0.0 prepared 9 November 2026. Target journal: Geomorphology. This is a local repository package prepared for deposit; no public repository URL or DOI is asserted.

## Contents and quick start

The `data/` folder contains 20 UTF-8 CSV tables. `metadata/data_dictionary.csv` defines every column. `metadata/table_catalog.json` maps each table to manuscript figures, tables and methods. Empty fields mean unavailable or undefined values. Booleans are written as True/False. Distances use metres or kilometres as specified; positive bed-level differences are upward.

Python 3.10+ is sufficient for the public checks and aggregate reproduction; no third-party packages are needed.

```shell
python code/verify_release.py
python code/reproduce_summaries.py --output results
```

The first command checks the manifest, checksums, keys, units-relevant identities and manuscript headline values. The second rebuilds a compact summary JSON and the full-period sector table from the included data. `results/` is generated locally and ignored by Git.

## Scientific scope

The core data contain 36 numbered profiles surveyed in 2009, 2010, 2011 and 2014. The 144 profile-interval rows comprise three adjoining intervals and the overlapping 2009-2014 summary. Every interval uses identical within-profile support and trapezoidal integration weights. Profiles are summarized with equal weight across the four positional sectors.

N measures signed endpoint difference, D and E its positive and negative magnitudes, G=D+E, C=1-|N|/G, and H measures the absolute departure from N. G is an endpoint difference, not accumulated sediment turnover. The 100 m analytical grid retains the underlying survey-resolution limitations.

The tables reproduce summary-level metrics, sector medians, sensitivity results, conditional error envelopes, waterline-pair denominators and matched environmental aggregates. Original bathymetric observations, geocoded per-survey profile arrays, complete Landsat rasters and original environmental downloads are held separately. Raw-survey redistribution permissions remain unresolved. Re-running the complete raw-data pipeline requires those inputs; the public checks operate on the deposited result tables. See `docs/REPRODUCIBILITY.md`.

## Error scenarios and waterlines

All scenario scales in `scenario_parameters.csv` are assumed per-survey errors. The no-change experiment uses 4000 draws per profile/scenario and seed 20261108. The separate joint waterline experiment uses 16000 shared-endpoint draws and seed 20261107. Their envelopes quantify conditional resolving power; they are not empirically calibrated instrument errors.

The annual inventory contains 496 candidate waterline intersections. Of 144 bathymetric interval records, 42 have both annual waterline endpoints. The optical boundary is an instantaneous waterline without tidal normalization. Exact bathymetric dates, common-datum transfer and independent registration checks constrain interpretation.

## Source attribution and reuse

Yonggui Yu provided research data and performed data processing. Survey provenance is described in Yu (2017), *Changes in Huanghe water and sediment delivery to the sea since the operation of Xiaolangdi Reservoir and its delta response*, PhD thesis, Ocean University of China. The underlying survey programme is attributed in the manuscript to the Yellow River Conservancy Commission.

Landsat product identifiers are included for tracing USGS Collection 2 sources accessed through Microsoft Planetary Computer. Wave context comes from ERA5-Ocean via the Open-Meteo historical marine service. The annual Lijin series is a secondary compilation from DOI 10.5281/zenodo.23796152 with the upstream column attributed to Wu (2021); it has not been independently reconciled against an official original annual series. Third-party data retain their source attribution and applicable terms. See `docs/PROVENANCE_AND_REUSE.md`.

Citation metadata are in `CITATION.cff`. No publication DOI or repository address has been invented. The package does not assign a blanket open-data licence to upstream survey or third-party materials; confirm the intended reuse licence before adding one to the repository.

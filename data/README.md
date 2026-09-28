# Dataset Setup

The raw vibration datasets are not stored in this repository.

## Phase I — CWRU Bearing Data

Official source: https://engineering.case.edu/bearingdatacenter/welcome

The selected subset contains four conditions across four motor loads:

| Class | Files / standardized labels |
|---|---|
| Normal | Normal_0 through Normal_3 |
| Inner race, 0.007 in | IR007_0 through IR007_3 |
| Ball, 0.007 in | B007_0 through B007_3 |
| Outer race, 0.007 in at 6:00 | OR007@6_0 through OR007@6_3 |

Approximate motor speeds by load are 1797, 1772, 1750, and 1730 rpm for 0, 1, 2, and 3 HP respectively.

The analysis uses drive-end vibration. Fault recordings are native 12 kHz. The selected normal drive-end recordings are effectively 48 kHz and are resampled to 12 kHz using `scipy.signal.resample_poly(..., up=1, down=4)` before feature extraction.

One-second non-overlapping windows are used.

## Phase II — NASA IMS Bearings

Official source: https://data.nasa.gov/dataset/ims-bearings

The project uses IMS Test 2 for the primary early-anomaly analysis and selected failed-bearing sensor trajectories from Test 1 for separate trajectory validation.

For Test 2, Bearing 1 is analyzed from the four-channel recordings. The final two recordings showed a simultaneous near-zero collapse across all channels and were treated as an acquisition/shutdown-state artifact for operating-degradation analysis.

For Test 1, recordings 1–156 are excluded because an observed approximately 148-hour acquisition gap separates them from the subsequent monitoring sequence. During monitored-time reconstruction, intervals above 10 minutes are capped at 10 minutes and persistence is reset after gaps above 20 minutes.

## Local Folder Layout

```text
data/
├── raw/              # CWRU raw .mat files
├── processed/        # generated CWRU feature data
├── ims_raw/          # extracted IMS data
└── ims_processed/    # generated IMS feature data
```

These directories are ignored by Git.

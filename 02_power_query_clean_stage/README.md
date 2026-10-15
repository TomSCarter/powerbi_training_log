# 02 – Power Query: cleaning stage

Re-implementing the cleaning stage of my UK Land Registry and EPC pipeline in Power Query, and comparing it with the original pandas version.

## Data

The input is the matched Price Paid and EPC dataset just before cleaning (91,150 sales). It isn't included because the EPC data licence restricts sharing address data.

To recreate it:

1. Run `export_pre_clean.py` in the [land-registry-cleaning-pipeline](https://github.com/TomSCarter/land-registry-cleaning-pipeline) (see that repo's README for setup).
2. Copy `data/processed/pre_clean_export.parquet` into this repo's top-level `data/` folder.
# 02 – Power Query: cleaning stage

Re-implementing the cleaning stage of my UK Land Registry and EPC pipeline in Power Query, and comparing it with the original pandas version.

## Data

The input is the matched Price Paid and EPC dataset just before cleaning (91,150 sales). It isn't included because the EPC data licence restricts sharing address data.

To recreate it:

1. Run `export_pre_clean.py` in the [land-registry-cleaning-pipeline](https://github.com/TomSCarter/land-registry-cleaning-pipeline) (see that repo's README for setup).
2. Copy `data/processed/pre_clean_export.parquet` into this repo's top-level `data/` folder.

## Spec

1. Convert invalid values to null
    1. Placeholders converted to null: PLACEHOLDERS = {'property_type': 'Not Recorded', 'built_form': 'Not Recorded', 'tenure': 'unknown'}
    2. 'number_heated_rooms' = 0 converted to null
    3. 'floor_height' < 1.5 m converted to null
2. Apply exclusions (as rules)
    1. exclude properties with total_floor_area <= 9 sqm
        - keep > 9 sqm
    2. exclude properties with total_floor_area > 2000 sqm AND (number_habitable_rooms <= 7  OR number_habitable_rooms is missing)
        - keep total_floor_area <= 2000 OR (number_habitable rooms > 7 AND number_habitable_rooms IS NOT NULL)
    3. exclude records with current_energy_efficiency > 110 and energy_consumption_current > 200 and property_type is in [Flat, Maisonette]
        - keep current_energy_efficiency <= 110 or energy_consumption_current <= 200 or property_type is not in [Flat, Maisonette]
    4. exclude records with construction_age_band < 4 characters (has no nulls)
        - keep construction_age_band >= 4 characters
3. Impute floor_height with whole-set median (after invalid values are set to null, exclusions are applied and ignoring nulls) and add floor_height_imputed flag (boolean: True for imputed, False otherwise)

# Notes

- Empty text box gives "" empty string not null
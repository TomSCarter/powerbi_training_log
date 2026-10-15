# Power BI training log

Power BI exercises from my data analytics training plan, covering Power Query, data modelling and DAX.

## Approach

Each exercise reuses a dataset I have already cleaned or analysed in Python, so I'm learning new tooling rather than solving new data problems at the same time. Where an exercise re-implements an existing pandas step, its README compares the two: what was easier, what was harder, and how Power Query's applied steps compare with a pandas pipeline. Each Power Query version is checked against counts recorded from the original pandas run.

## Exercises

| # | Exercise | Skills | Status |
|---|---|---|---|
| 01 | [Flu vaccination visual](01_flu_vaccination_visual/) | Rebuilding a visual from my Week 8 capstone | Complete |
| 02 | [Power Query: cleaning stage](02_power_query_clean_stage/) | Power Query, M, conditional logic, imputation | In progress |
| 03 | [Star schema and DAX](03_star_schema_dax/) | Data modelling, relationships, DAX measures | Planned |

## Related repositories

- [land-registry-cleaning-pipeline](https://github.com/TomSCarter/land-registry-cleaning-pipeline): UK Land Registry Price Paid and EPC matching and cleaning pipeline in pandas, the source of the data for exercise 02
- [sql_training_log](https://github.com/TomSCarter/sql_training_log): SQL practice log

## Data

Data files are not included. The Land Registry Price Paid data is published under the Open Government Licence, but the EPC data licence restricts redistributing address data, so the matched dataset can't be shared. Each exercise README explains how to recreate its input from the original sources and links to the relevant pipeline code. Screenshots show the results.

## Tools

- Power BI Desktop, with work saved in Power BI Project (`.pbip`) format so queries and model definitions are stored as text and can be version-controlled

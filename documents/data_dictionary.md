# Data Dictionary

## fact_parking_transactions

Daily aggregated parking meter transactions by meter (2023–2026).

| Field | Type | Description |
|---|---|---|
| pole_id | Text | Unique meter identifier, joins to `dim_meter_location` |
| date | Date | Transaction date, joins to `dim_date` |
| year | Whole Number | Transaction year |
| month | Whole Number | Transaction month |
| day | Whole Number | Transaction day |
| sum_trans_amt | Fixed Decimal Number | Total revenue for that meter/day, in dollars |
| num_trans | Whole Number | Count of transactions for that meter/day |

## dim_meter_location

One row per parking meter, describing its location and configuration.

| Field | Type | Description |
|---|---|---|
| pole_id | Text | Unique meter identifier, joins to `fact_parking_transactions` |
| zone | Text | Meter zone (e.g., Downtown, Uptown); "Unknown" for meters missing source location data |
| area | Text | Meter neighborhood/area (e.g., East Village, Marina); "Unknown" for meters missing source location data |
| sub_area | Text | Street/block-level identifier |
| latitude | Decimal Number | Meter latitude |
| longitude | Decimal Number | Meter longitude |
| configuration_id | Whole Number | Identifier for the meter's rate/configuration setup |
| configuration_name | Text | Description of the meter's rate/configuration setup |
| days_in_operation | Text | Days of the week the meter is enforced |
| time_start | Time | Enforcement start time |
| time_end | Time | Enforcement end time |
| time_limit | Text | Maximum parking duration allowed |
| price | Text | Meter rate |
| restrictions | Text | Any additional posted restrictions |
| mobile_pay | Text | Indicates whether the meter supports mobile payment |
| multi_space | Text | Indicates whether the meter is single-space or multi-space |

## dim_date

Custom calendar table covering 2023–2026.

| Field | Type | Description |
|---|---|---|
| date | Date | Calendar date, joins to `fact_parking_transactions` |
| year | Whole Number | Calendar year |
| month_number | Whole Number | Calendar month (1-12) |
| month_name | Text | Month name (e.g., "January") |
| day_number | Whole Number | Day of month |
| day_of_week | Text | Day name (e.g., "Monday") |
| day_of_week_number | Whole Number | Numeric day of week, used to sort `day_of_week` correctly |
| quarter | Text | Calendar quarter (e.g., "Q2") |
| is_weekend | Boolean | TRUE if Saturday/Sunday |

## Key Measures

| Measure | Definition |
|---|---|
| total revenue | Sum of `sum_trans_amt` |
| total transactions | Sum of `num_trans` |
| revenue per meter | Total revenue ÷ distinct count of `pole_id` |
| revenue py | Total revenue for the same period, prior year |
| revenue yoy % | Year-to-date % change in total revenue vs. the same year-to-date period last year (accounts for 2026 being a partial year) |
| avg daily revenue | Average of total revenue across distinct dates |

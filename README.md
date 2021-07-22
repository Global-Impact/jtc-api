## Using JTC API

1.) Generate an API key `https://global-impact-prod.revelry-prod.revelry.net/user/api-key` (available for admins only)

2.) Use the generated api key as an auth-bearer token in your request

## IRR Score Endpoint
```
curl --location --request POST 'https://global-impact-prod.revelry-prod.revelry.net/api/irr_score' \
--header 'Authorization: Bearer global_impact.7scqOkI-.vdajs7tzit1KkAo_' \
--header 'Content-Type: application/json' \
--data-raw '{
    "impact_multiplier": 0.8,
    "units_delivered": 120320,
    "goal": 300,
    "time_period": 3,
    "cost": 21312312321,
    "log_base": 100
}'
```
### Impact Potential Endpoint
```
curl --location --request POST 'https://global-impact-prod.revelry-prod.revelry.net/api/impact_potential' \
--header 'Authorization: Bearer global_impact.CiSHk_JR.RLzthaeGz1ATpKKP' \
--header 'Content-Type: application/json' \
--data-raw '{
    "accessibility": 0,
    "educational_attainment": 2,
    "household_income_vs_national_median": 1,
    "inequality": 0,
    "poverty": 4,
    "resident_demographic": 2,
    "unemployment_vs_national_average": 3,
    "fossil_fuel_energy_use": 2
}'
```
Available fields for impact potential:
- `accessibility`
- `educational_attainment`
- `household_income_vs._national_median`
- `inequality`
- `poverty`
- `resident_demographic`
- `unemployment_vs._national_average`
- `walkability`
- `fossil_fuel_energy_use`
- `housing_cost_burden`
- `housing_rentals`

Each metric must be scored 0 - 5. JTC Impact Potential utilizes 8 of the available 11 metrics, and the API will tabulate the first 8 metrics with scores.

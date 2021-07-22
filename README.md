
|            | Build Status                                                                                                                                      |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Staging    | [ ! [![Build Status](https://travis-ci.com/revelrylabs/global-impact.svg?token=GsQt5YRsdYHuzuKaDJxg&branch=main)](https://travis-ci.com/revelrylabs/global-impact) |
| Production | [ ! [![Build Status](https://travis-ci.com/revelrylabs/global-impact.svg?token=GsQt5YRsdYHuzuKaDJxg&branch=main)](https://travis-ci.com/revelrylabs/global-impact)  |

[![Coverage Status](https://opencov.prod.revelry.net/projects/49/badge.svg)](https://opencov.prod.revelry.net/projects/49)

# Global Impact

* **Project Start Date:** May 3, 2021
* **Project Duration:** 12 weeks
* **Current End of Contract Date:** July 23, 2021

## Team
Role | Person | Email
---- | --- | ---
Partner/Product Owner |Howard W. Buffett|hwb@globalimpact.co
Product Manager|Amanda Phu|amanda.phu@revelry.co
Engineer Coach|Stuart|stuart.ballard@revelry.co
Engineer|Ian Adams|ian.adams@revelry.co
Engineer|Justin Scott|justin.scott@revelry.co
Designer|Dan Murphy|dan.murphy@revelry.co
Engineer Apprentice|PJ DiIorio|pj.diiorio@revelry.co

## Links to relevant docs, repos, etc.

| Thing                            | Location                                                                                                                                 |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| Project Board                    | [Link](https://github.com/revelrylabs/global-impact/projects/1)|
| Google Drive                     | [Link](https://drive.google.com/drive/folders/1QPu2oaIRI07AseFjEWo95OGPeTNV1C6k?usp=sharing) |
| Sprint Reports                   | [Link](https://drive.google.com/drive/folders/19gHW3wVU71pLMPWPLQoVa131wopzw6Gl?usp=sharing)|
| Interview Checklist and Scripts  | [Link](https://drive.google.com/drive/folders/19BdiMuJ1V3kBRycrcf9b0mW93Hu3kXJr?usp=sharing)|
| Customer Validation Board        | [Link](https://drive.google.com/drive/folders/1X4-P5OHtM8dQnboWrYN1KKRSkhyKCV7U?usp=sharing)|
| Continuous Integration           | [https://travis-ci.com/github/revelrylabs/global-impact](https://travis-ci.com/github/revelrylabs/global-impact)|
| Production                       | [https://global-impact-prod.revelry-prod.revelry.net/](https://global-impact-prod.revelry-prod.revelry.net/)|
| Staging                          | [https://global-impact-staging.revelry-prod.revelry.net/](https://global-impact-staging.revelry-prod.revelry.net/)|
| Keybase                          | [keybase://team/revelrylabs/Global%20Impact](keybase://team/revelrylabs/Global%20Impact)|   
| Postman Collection               | [https://github.com/revelrylabs/global-impact/blob/main/assets/api_spec/postman_collection.json](https://github.com/revelrylabs/global-impact/blob/main/assets/api_spec/postman_collection.json)|   

## Compatibility Targets
### Web App Browser Compatibility Targets

OS | Browsers
--- | ---
Windows | Chrome (latest), Firefox (latest), Edge (latest)
Mac | Chrome (latest), Firefox (latest), Safari (latest)
iOS | Safari (latest)
Android | Chrome (latest)

## The Project Brief
### The Idea
Global Impact calculates the Impact Rate of Return (iRR) to determine past or future societal, environmental, and governance-related impact. They have a formula which currently lives in Excel. We are partnering with Global Impact to build a web based application to calculate iRR. Uesrs should be able to login, build projects which all users in the organization can share, create an iRR configuration (algorithm), enter project data, and calculate the iRR.

### Who are we building for?
Initially, our focus is to build for Global Impact internal use, API integration with their current client/partner, JTC Americas, and Opportunity Zone Funds.

### What is the main problem we are trying to solve?
How might we automate and guide users (Consultant [Global Impact], Data Providers/Aggregator, Project implementer, Project Investor/Grant Maker) in the process of defining, tracking, analyzing, managing, and reporting their impact so that they may make lasting improvements on societal and environmental challenges?

### Core Loop
[Link](https://github.com/revelrylabs/global-impact/blob/main/bpmn/images/global_impact.png)

## Nouns & Verbs
[Link](https://github.com/revelrylabs/global-impact/blob/main/nouns_and_verbs.md)

## Tech Stack

- Elixir
- Phoenix Web Framework

## Project Setup

Project can be set up by running `sh ./bin/setup`. It does the steps defined below.
Note that Elixir 1.5 or greater is required in order to start it.

Once run, follow directions and start app by running `sh ./bin/server`

Now you can visit [`localhost:4000`](http://localhost:4000) from your browser.                                                                                                  |

## Data import

Iniaially the bulk of the meta-data required to setup a calculator will be imported via scripts. There are mix tasks as well as jobs for flux to execute upon deployment. The data itself is currently included within the repository with future plans to build uploads and additional administrative functionality.

Each kind of import has a folder within `priv/repos/imports` and all imports should execute upon every file within it's data folder. Optionally the mix commands can be given another path/file for development purposes. Currently all data is expected to be provided in CSV format

- Tag Imports
  - Data: `priv/repos/imports/tags/*`
  - Mix: `mix global_impact.import_tags`
  - Main Module: `GlobalImpact.Kiis.ImportTags`
- KII Imports
  - Data: `priv/repos/imports/kiis/*`
  - Mix: `mix global_impact.import_kiis`
  - Main Module: `GlobalImpact.Kiis.ImportKiis`
- Metrics Imports
  - Data: `priv/repos/imports/oz/*`
  - Mix: `mix global_impact.import_oz`
  - Main Module: `GlobalImpact.ImportOz`

## Using JTC API
[Postman Collection](https://github.com/revelrylabs/global-impact/blob/main/assets/api_spec/postman_collection.json)
1.) Generate an API key `https://global-impact-staging.revelry-prod.revelry.net/user/api-key` (available for admins only)
2.) Use the generated api key as an auth-bearer token in your request
## IRR Score Endpoint
```
curl --location --request POST 'https://global-impact-staging.revelry-prod.revelry.net/api/irr_score' \
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
curl --location --request POST 'https://global-impact-staging.revelry-prod.revelry.net/api/impact_potential' \
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

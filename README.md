# Los Angeles County Condo Building Register and condo age by city

2,772 Los Angeles County condominium buildings with 20 or more condo units, compiled by LA Condo HQ from the LA County Assessor's 2026 parcel roll: unit count, year built, living-area range and bedroom mix by address. This repository also holds the city table of LA Condo HQ's LA County condo age report 2026: for each city, the condominium projects of 20 or more units, their units, and how many were built before 1996.

LA Condo HQ is published by Eltherion, LLC. It is an independent research website, not a condo association or management company.

## Canonical pages

| What | Page |
| --- | --- |
| The building register, with the CSV download and how to cite it | https://lacondohq.com/condo-buildings |
| LA County condo age report 2026 | https://lacondohq.com/research/la-condo-age-report |
| Data sources and methodology | https://lacondohq.com/methodology |
| Archived snapshot of the register CSV (Zenodo) | https://doi.org/10.5281/zenodo.23924770 |

## Files

All files were downloaded on 2026-11-13 and are kept exactly as published. The file names are the download names the site sends. SHA-256 checksums are in `CHECKSUMS.txt`.

| File | Published at | Data rows | Columns |
| --- | --- | --- | --- |
| `data/la-county-condo-building-register.csv` | https://lacondohq.com/condo-buildings/data.csv | 2,772 | 16 |
| `data/la-county-condo-age-by-city.csv` | https://lacondohq.com/research/la-condo-age-report/cities.csv | 122 | 6 |

Format notes, from the files themselves:

- The register file has one header line and uses CRLF line endings.
- The city file starts with one comment line that begins with `#`, then the header line. Skip the first line when loading it (for example `pandas.read_csv(path, skiprows=1)`). The comment line reads: `# LA County condo age report: Los Angeles County Assessor, Assessor Parcel Data Roll 2026, checked 2026-10-30. Source: LA Condo HQ (Eltherion, LLC).`

The two files count different things. The register lists buildings by address. The city table counts condominium projects, which the report builds "by grouping the Los Angeles County Assessor's condominium parcels by recorded tract or parcel map."

## Source of the underlying records

Both files are built from one source, as the live pages name it: [Los Angeles County Assessor, Assessor Parcel Data Roll 2026](https://www.arcgis.com/home/item.html?id=0d3ac33a76e1495bb7fc522a8085729c).

| File | Checked |
| --- | --- |
| Building register | 2026-11-12, as the register page states |
| City table | 2026-10-30, as the report page and the file's first line state |

## Columns

### la-county-condo-building-register.csv

The register page says the file holds only the public fields shown on each building's page. The building pages say: "The Assessor counts each condominium unit as its own parcel; these figures summarize the parcels at this address."

| Column | Meaning | First row | Blank cells |
| --- | --- | --- | --- |
| `address` | Street address of the building | `901 10th St` | 0 |
| `city` | City. The city pages say: "City is the situs city the Assessor records." | `Santa Monica` | 0 |
| `zip` | ZIP code | `90403` | 1 |
| `condo_units` | Condominium units at the address | `34` | 0 |
| `year_built_min` | Year built on the roll, earliest among the units at the address | `1970` | 4 |
| `year_built_max` | Year built on the roll, latest among the units at the address. Where the two years differ the building page shows both, for example "built 1973 to 1997" for 937 12th St, Santa Monica. | `1970` | 4 |
| `living_area_sqft_min` | Living area of the smallest unit, in square feet | `1022` | 4 |
| `living_area_sqft_median` | Median living area of the units, in square feet | `1380` | 4 |
| `living_area_sqft_max` | Living area of the largest unit, in square feet | `1555` | 4 |
| `studios` | Units that are studios | `0` | 0 |
| `one_bedroom` | Units with one bedroom | `6` | 0 |
| `two_bedroom` | Units with two bedrooms | `24` | 0 |
| `three_bedroom` | Units with three bedrooms | `4` | 0 |
| `four_plus_bedroom` | Units with four or more bedrooms | `0` | 0 |
| `bedrooms_not_recorded` | Units with no bedroom count recorded. The value is 0 in every row of this file. | `0` | 0 |
| `page_url` | The building's page on lacondohq.com | `https://lacondohq.com/condo-buildings/901-10th-st-santa-monica-90403` | 0 |

### la-county-condo-age-by-city.csv

| Column | Meaning | First row |
| --- | --- | --- |
| `city` | City. The report says cities follow the roll's situs city. | `Los Angeles` |
| `condo_projects_20_plus_units` | Condominium projects with 20 or more units | `1544` |
| `units` | Units in those projects | `83169` |
| `projects_built_before_1996` | Projects built before 1996 | `1253` |
| `units_built_before_1996` | Units in the projects built before 1996 | `67136` |
| `share_of_units` | `units_built_before_1996` as a share of `units`, written as a decimal | `0.8072` |

## Method

From the LA County condo age report:

> Counts cover every condominium project with 20 or more units in our register, built by grouping the Los Angeles County Assessor's condominium parcels by recorded tract or parcel map. A project's year is the year built on the roll; where its parcels differ, the most common year is used. Older means built before 1996. Cities follow the roll's situs city.

## Caveats stated on the live pages

- The figures are not a count of inspections due. "The roll does not describe balconies, framing or inspections, so these figures are not a count of SB 326 inspections due."
- "6 projects with no year built on the roll are left out."
- "A year built and a unit count say nothing about a building's condition, framing, inspection results, reserves or charges."
- The building figures "say nothing about the HOA's finances, rules or dues, or about units for sale."
- "The Assessor's roll doesn't name associations."

## Updates

The LA Condo HQ methodology page says county records are "updated when we re-run or review them, with the check date shown beside the information." The register page says: "Cite the DOI for a fixed version, or the page for the latest data." The files in this repository are the copies downloaded on 2026-11-13; the pages above have the latest data.

## How to cite

The register, as its page gives it:

> LA Condo HQ (Eltherion, LLC). Los Angeles County Condo Building Register, compiled from the Los Angeles County Assessor, Assessor Parcel Data Roll 2026, checked November 12, 2026. https://lacondohq.com/condo-buildings. Archived snapshot: https://doi.org/10.5281/zenodo.23924770

The register page adds: "A dated snapshot of this file is archived on Zenodo with a permanent DOI: 10.5281/zenodo.23924770 (deposited 2026-11-03)."

The city table, as the LA County condo age report gives it:

> LA Condo HQ (Eltherion, LLC), LA County condo age report 2026, from the Los Angeles County Assessor roll checked 2026-10-30.

A machine-readable citation is in `CITATION.cff`.

## License

The LA County condo age report says: "City figures are free to reuse with that credit." This compilation is released under the Creative Commons Attribution 4.0 International license (CC BY 4.0); see `LICENSE`. Credit LA Condo HQ (Eltherion, LLC) as shown above. The underlying records are public records from the Los Angeles County Assessor.

## Corrections

From the methodology page: "If something here is wrong, email hello@lacondohq.com with the page address, the statement in question and a supporting public source."

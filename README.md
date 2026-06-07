# paris-1871

This repository contains from judicial records of repressed Paris communards of the Paris Commune of 1871. It contains any publically accessible data, as well as pointers to where to find publically inaccessible data in the archives.

The entirety of this dataset has been compiled from Jean-Claude Farcy's project, found at communards-1871.fr. A full citation is available at the bottom of this document. It has also been augmented, e.g. by adding the addresses of communards.

Such a dataset is useful for research examining how the Commune was repressed.

There are n=41,375 individual communards in the dataset. They are all in a singular csv.
## Codebook

| Field | Type | Description |
|---|---|---|
| Profile_URL | string | Link to individual profile from "La répression judiciaire de la Commune de Paris : des pontons à l’amnistie (1871–1880)" |
| Raw_Bio_Text | string | Raw extracted biography text for each communard |
| Âge déclaré | string | Age declared by the communard at arrest (raw) |
| Âge calculé au 31 mai 1871 | string | Age calculated by authorities on 31/05/1871 (usually more reliable) |
| age | integer | Cleaned numeric age (derived from above) |
| État civil | string | Marital status |
| Père | string | Father's name |
| Mère | string | Mother's name |
| Adresse | string | Raw address string as recorded in sources |
| Profession civile | string | Civilian occupation (raw) |
| Profession militaire | string | Military occupation (raw) |
| Type d’activité | string | Sector or activity type (e.g., garments) |
| Branche | string | Broad sector (e.g., industry, commerce, transport) |
| Garde nationale | string | Raw national guard battalion/rank string |
| national_guard_rank | string | Parsed rank within the National Guard |
| national_guard_batallion | integer | Parsed battalion number for the National Guard |
| Communard_particulièrement_recherché_par_les_autorités_(motif) | string | Reason(s) for being specially sought by Thiers' government |
| Date d’arrestation | string (dd/mm/yyyy) | Arrest date; stored as string in `dd/mm/yyyy` format |

### Address components (parsed)
| Field | Type | Description |
|---|---|---|
| add_city | string | City portion of the address (overwhelmingly "Paris") |
| add_department | string | Department portion of the address (overwhelmingly "Seine") |
| add_house_number | integer | House number, when available |
| add_street | string | Street name; set to "Paris - Seine" when no specific street recorded |
| add_quartier | string | Quartier (neighborhood) portion of address |
| arrondissement | integer | Arrondissement number |

### Geocoding
| Field | Type | Description |
|---|---|---|
| latitude | real | Latitude of the matched address (from adresse.data.gouv.fr) |
| longitude | real | Longitude of the matched address |
| confidence_score | real | Confidence score returned by adresse.data.gouv.fr for the match |
| match_type | string | Most granular match level (e.g., housenumber, street, locality) |

## Archival details
The following fields indicate where related archival files can be found in French archives:

| Field | Description |
|---|---|
| Archives du Service historique de la Défense | Location of the communard's file in the Service historique de la Défense (Vincennes) |
| Archives nationales d’Outre-mer | Location of the communard's file in the Archives nationales d'Outre-mer |
| Archives nationales, dossiers de grâce | Location of pardon/clemency files in the French National Archives (Paris) |

## Notes
- Geocoding source: https://adresse.data.gouv.fr/ (government address database). |
- Date fields are stored as strings in the original dataset; convert to ISO or datetime objects before temporal analysis. |
- Field names preserve original French labels where present; cleaned/parsed fields use ASCII-friendly names (e.g., `age`, `add_street`).


## Citation
```
Farcy, J.-C. (2019, September 26). La répression judiciaire de la Commune de Paris : des pontons à l'amnistie (1871-1880). LIR3S, Université Bourgogne Europe. https://communards-1871.fr/index.php
```
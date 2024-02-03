# Scrape ATC codes from WHO Collaborating Centre for Drug Statistics Methodology 

This repository provides a script to scrape the WHO Collaborating
Centre for Drug Statistics Methodology
[website](https://www.whocc.no/atc_ddd_index). It reads ATC codes and
their information, and writes them to a flat CSV file.

The script recursively runs down the hierarchy from an input ATC
code. For example, if provided with "C10", it will download C10 and
all subcodes under C10.
  
From ATC levels 1 to 4, you get the codes and names of all classes. At
ATC level 5, some but not all entries have the additional fields
Administration Route, Defined Daily Dose (DDD), and Note; these will
also be scraped if present.

## Usage

1) clone the repository

2) install R

3) install the 'pacman' package (from within the R shell)

```install.packages("pacman")```

4) run the script

```Rscript ./atcd.R```

## Scraping results

As of Feb 3rd, 2024 there are **6,807** unique ATC codes and 5,956
unique names in the WHO website. Here is a breakdown by ATC level:

| ATC level | Codes | Names |
|:----------|------:|------:|
| Level 1   | 14    | 14    |
| Level 2   | 94    | 94    |
| Level 3   | 271   | 266   |
| Level 4   | 933   | 863   |
| Level 5   | 5495  | 4756  |
  
An example of a name with multiple codes is "miconazole", which has
codes
[A01AB09](https://www.whocc.no/atc_ddd_index/?code=A01AB09&showdescription=no),
[A07AC01](https://www.whocc.no/atc_ddd_index/?code=A07AC01&showdescription=no),
[D01AC02](https://www.whocc.no/atc_ddd_index/?code=D01AC02&showdescription=no),
[G01AF04](https://www.whocc.no/atc_ddd_index/?code=G01AF04&showdescription=no),
[J02AB01](https://www.whocc.no/atc_ddd_index/?code=J02AB01&showdescription=no),
[S02AA13](https://www.whocc.no/atc_ddd_index/?code=S02AA13&showdescription=no).
  

If you just need all ATC classes and data in one big table, you can
download the CSV file in the original
[repository](https://github.com/fabkury/atcd/raw/master/WHO%20ATC-DDD%202021-12-03.csv).
However, remember that the WHO website is updated over time.
  
## About the license of the ATC-DDD data  

The WHO Collaborating Centre for Drug Statistics (WHOCC)
[sells](https://www.whocc.no/atc_ddd_index_and_guidelines/order)
electronic files (e.g. Excel spreadsheet) containing the entire
ATC-DDD index. They also publish the same data for free on their
website. Their [copyright
disclaimer](https://www.whocc.no/copyright_disclaimer), in my layman's
opinion, seems to permit web scraping as long as no commercial
activity is involved. The license of this GitHub repository precludes
commercial use, and in addition to that the contents of the WHOCC
website are not being modified but just written as-is to a
file. Therefore, to my understanding, there is no violation of the
WHOCC website's copyright statement.

## LICENSE

This repository has been
[forked](https://github.com/fabkury/atcd.git); the original version
was released under the Creative Commons
Attribution-ShareAlike-NonCommercial 4.0 International
[license](https://creativecommons.org/licenses/by-nc-sa/4.0/) (CC
BY-NC-SA 4.0).

The current version of the repository has its full text
[license](LICENSE) here; what follows are the copyright and license
notices.

```
Copyright (C) 2024 Federico Motta <federico.motta@unimore.it>
              2023 Fabrício Sampaio Peres Kury <github@kury.dev>
              2022 Fabrício Sampaio Peres Kury <github@kury.dev>
              2021 Fabrício Sampaio Peres Kury <github@kury.dev>
              2020 Fabrício Sampaio Peres Kury <github@kury.dev>

This script is free software: you can redistribute it and/or modify it
under the terms of the GNU General Public License as published by the
Free Software Foundation, either version 3 of the License, or (at your
option) any later version.

This script is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
General Public License for more details.

You should have received a copy of the GNU General Public License
along with this script.  If not, see https://www.gnu.org/licenses/
```
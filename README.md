# Librela Adverse Drug Reaction & VeDDRA Data

This repository contains contains the code and input/output files for suspected adverse drug reactions (`sADR`s) from [Bedinvetmab (Librela)](https://en.wikipedia.org/wiki/Bedinvetmab). 

The data itself is downloaded from [EudraVigilance’s Database of Suspected Adverse Drug Reaction Reports](https://www.adrreports.eu/vet/en/index.html), colloquially known as **EVVet**. As of the publication of this repository, EVVet continues to be the most comprehensive (official) source of adverse drug reactions for Librela, the vast majority of them reported by Veterinarians and healthcare professionals.

The following countries are included in the data:
> 🇦🇩 Andorra 🇦🇺 Australia 🇦🇹 Austria 🇧🇪 Belgium 🇧🇷 Brazil 🇧🇬 Bulgaria 🇨🇦 Canada 🇰🇾 Cayman Islands 🇨🇱 Chile 🇨🇴 Colombia 🇭🇷 Croatia 🇨🇿 Czech Republic 🇩🇰 Denmark 🇪🇨 Ecuador 🇪🇪 Estonia 🇫🇮 Finland 🇫🇷 France 🇩🇪 Germany 🇬🇷 Greece 🇭🇺 Hungary 🇮🇸 Iceland 🇮🇪 Ireland 🇮🇱 Israel 🇮🇹 Italy 🇯🇵 Japan 🇱🇹 Lithuania 🇱🇺 Luxembourg 🇲🇽 Mexico 🇳🇱 Netherlands 🇳🇨 New Caledonia 🇳🇿 New Zealand 🇳🇴 Norway 🇵🇱 Poland 🇵🇹 Portugal 🇸🇬 Singapore 🇸🇮 Slovenia 🇿🇦 South Africa 🇪🇸 Spain 🇸🇪 Sweden 🇨🇭 Switzerland 🇹🇭 Thailand 🇬🇧 United Kingdom 🇺🇸 United States

Additionally, it also provides a `csv` version of the [Combined VeDDRA list of clinical terms for reporting suspected adverse events in animals and humans to veterinary medicinal products](https://www.ema.europa.eu/en/documents/regulatory-procedural-guideline/combined-veterinary-dictionary-drug-regulatory-activities-veddra-list-clinical-terms-reporting-suspected-adverse-events-animals-and-humans-veterinary-medicinal-products_en.pdf) filtered only on (A)nimal and (C)ommon terms. Simply put, this is the list of all possible adverse reactions categorized by organ systems, etc. 

### 📥 Download

The consolidated data is provided as a [`csv`](https://en.wikipedia.org/wiki/Comma-separated_values) (supported by Excel). You can download it here (right-click > download):<br/>
[`data/output/evvet_master.csv →`](https://github.com/open-adr/librela/raw/main/data/output/evvet_master.csv)

Additionally, you can also download the VeDDRA `csv`:<br/>
[`data/output/veddra.csv →`](https://github.com/open-adr/librela/raw/main/data/output/veddra.csv)

### 👀 Preview

This data feeds an [Observable](https://observablehq.com/) notebook that enables visualization, search, and download of the data itself. You can access it here:<br />
[`https://observablehq.com/@openadr/librela →`](https://observablehq.com/@openadr/librela)

### 🍳 How The Data Is Prepared

Provenance of the original EVVet data, including the contents of each cell, is considered sacred and treated as immutable. Our end-the-end process involves minimal merging and sanitizing of the data to facilitate analysis as follows:

1. We download `csv` files from [`EVVet’s Line Listing Tool`](https://dap.ema.europa.eu/analytics/saw.dll?Dashboard&PortalPath=%2Fshared%2FEVVET3%20PW%20NEW%2FDashboards%2FPublic%20Reports%2FPWS%2FPWS%2EReports&P1=dashboard&Action=Navigate&col1=%22Product%22.%22Product%20ShortName%22&val1=%22LIBRELA%22&psa1=%22EVVET3%20PR%20NEW%22&var2=dashboard.variables%5B%27product%27%5D&cov2=%22Product%22.%22Product%20ShortName%22&val2=%22LIBRELA%22&psa2=%22EVVET3%20PR%20NEW%22). This results in multiple `csv` files (split by year) that you can find in [`data/input/evvet/`](https://github.com/open-adr/librela/tree/main/data/input/evvet).
2. The [`data/fetch-evvet-data.ipynb`](https://github.com/open-adr/librela/blob/main/data/fetch-evvet-data.ipynb) `python` notebook iterates through all the source `csv` files, sanitizes them (concatenate, rearrange columns, drop duplicates, etc.), generates the [`evvet_master.csv`](https://raw.githubusercontent.com/open-adr/librela/main/data/output/evvet_master.csv) output file, and spits out some validation stats to ensure parity with EVVet (which is the source of truth).
 
As for VeDDRA terms, we downloaded the source `xlsx` file [linked on page 2 here](https://www.ema.europa.eu/en/documents/regulatory-procedural-guideline/combined-veterinary-dictionary-drug-regulatory-activities-veddra-list-clinical-terms-reporting-suspected-adverse-events-animals-and-humans-veterinary-medicinal-products_en.pdf), and converted it to a `csv` while filtering out human terms. You can see the trivial `notebook` that does that work here: [`data/veddra.ipynb`](https://github.com/open-adr/librela/blob/main/data/veddra.ipynb)

---

### ✉️ Contact  

If you have questions/concerns, contact [openadverseevents@gmail.com](mailto:openadverseevents@gmail.com). 

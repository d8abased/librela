# Librela & Solensia Adverse Drug Reaction & VeDDRA Data

This repository contains the code and input/output files for suspected adverse drug reactions (`sADR`) from [Bedinvetmab (Librela)](https://en.wikipedia.org/wiki/Bedinvetmab) and [Frunevetmab (Solensia)](https://en.wikipedia.org/wiki/Frunevetmab).

The data is sourced from [EudraVigilance’s Database of Suspected Adverse Drug Reaction Reports](https://www.adrreports.eu/vet/en/index.html), also known as **EVVet**. EVVet remains the most timely and comprehensive official source of adverse drug reactions for both Librela and Solensia, primarily reported by veterinarians and healthcare professionals.

The following countries are included in the data for Librela and Solensia (note: availability differs by country):
> 🇦🇩 Andorra 🇦🇺 Australia 🇦🇹 Austria 🇧🇪 Belgium 🇧🇷 Brazil 🇧🇬 Bulgaria 🇨🇦 Canada 🇰🇾 Cayman Islands 🇨🇱 Chile 🇨🇴 Colombia 🇭🇷 Croatia 🇨🇿 Czech Republic 🇩🇰 Denmark 🇩🇴 Dominican Republic 🇪🇨 Ecuador 🇪🇪 Estonia 🇫🇮 Finland 🇫🇷 France 🇩🇪 Germany 🇬🇷 Greece 🇭🇺 Hungary 🇮🇸 Iceland 🇮🇪 Ireland 🇮🇱 Israel 🇮🇹 Italy 🇯🇵 Japan 🇱🇹 Lithuania 🇱🇺 Luxembourg 🇲🇽 Mexico 🇳🇱 Netherlands 🇳🇨 New Caledonia 🇳🇿 New Zealand 🇳🇴 Norway 🇵🇱 Poland 🇵🇹 Portugal 🇸🇬 Singapore 🇸🇮 Slovenia 🇿🇦 South Africa 🇪🇸 Spain 🇸🇪 Sweden 🇨🇭 Switzerland 🇹🇭 Thailand 🇬🇧 United Kingdom 🇺🇸 United States

Additionally, the repository provides a `csv` version of the [Combined VeDDRA list of clinical terms for reporting suspected adverse events in animals and humans to veterinary medicinal products](https://www.ema.europa.eu/en/documents/regulatory-procedural-guideline/combined-veterinary-dictionary-drug-regulatory-activities-veddra-list-clinical-terms-reporting-suspected-adverse-events-animals-and-humans-veterinary-medicinal-products_en.pdf), filtered to include only (A)nimal and (C)ommon terms.

### 🌟 Features

- Comprehensive ADR Data: Access consolidated reports of adverse drug reactions for both Librela and Solensia, pulled from authoritative sources.
- Global Coverage: Data spans multiple countries, ensuring a broad and inclusive dataset.
- Up-to-Date: The repository is regularly updated to reflect the latest reported data.
- Interactive Visualization: Explore the data visually using integrated tools that make analysis accessible and engaging.
- VeDDRA Integration: Easily cross-reference adverse reactions with the Veterinary Dictionary for Drug Regulatory Activities (VeDDRA) for standardized clinical terms.

### 📂 Repository Structure

The repository is structured to help you easily locate and use the data:

```
librela/                        
├── data/                        # Jupyter Notebooks for data processing and analysis
    ├── input/
    │   ├── evvet/               # Raw EVVet data files
    │   │   ├── librela/         # Librela-specific data by year
    │   │   ├── solensia/        # Solensia-specific data by year
    │   └── veddra/              # VeDDRA reference files
    ├── output/
        ├── evvet/               # Processed EVVet data
            ├── librela/         # Processed Librela data
            ├── solensia/        # Processed Solensia data

```


### 📥 Download

Consolidated data is provided as `csv` files for both Librela and Solensia. You can download the latest files here (right-click > download):

- [Librela CSV →](https://github.com/d8abased/librela/raw/main/data/output/evvet/librela.csv)
- [Solensia CSV →](https://github.com/d8abased/librela/raw/main/data/output/evvet/solensia.csv)
- [VeDDRA CSV →](https://github.com/d8abased/librela/raw/main/data/output/veddra.csv)


### 👀 Preview

This data supports a collection of [Observable](https://observablehq.com/) notebooks for visualization, search, and download of the data. You can access these visualizations here: [https://librela.d8abased.com](https://librela.d8abased.com)

### 🍳 How The Data Is Prepared

The provenance of the original EVVet data, including the contents of each cell, is considered sacred and treated as immutable. Our process for preparing the data includes minimal merging, sanitizing, and augmenting to facilitate analysis:

1. **VeDDRA List Processing**: We perform a one-time download of the VeDDRA `xlsx` file and convert it to a `csv`, filtering out human terms. The resulting file is stored as [`veddra.csv`](https://github.com/d8abased/librela/raw/main/data/output/veddra.csv). The conversion notebook can be found [here](https://github.com/d8abased/librela/blob/main/data/veddra.ipynb).

2. **EVVet Data Collection**: `csv` files are downloaded from the [EVVet Line Listing Tool](https://dap.ema.europa.eu/analytics/saw.dll?Dashboard&PortalPath=%2Fshared%2FEVVET3%20PW%20NEW%2FDashboards%2FPublic%20Reports%2FPWS%2FPWS%2EReports&P1=dashboard&Action=Navigate&col1=%22Product%22.%22Product%20ShortName%22&val1=%22LIBRELA%22&psa1=%22EVVET3%20PR%20NEW%22&var2=dashboard.variables%5B%27product%27%5D&cov2=%22Product%22.%22Product%20ShortName%22&val2=%22LIBRELA%22&psa2=%22EVVET3%20PR%20NEW%22) for both Librela and Solensia. The files are then organized by year in the [`data/input/evvet/`](https://github.com/d8abased/librela/tree/main/data/input/evvet) directory.

3. **Data Processing**: The [`evvet.ipynb`](https://github.com/d8abased/librela/blob/main/data/evvet.ipynb) notebook processes the EVVet data by concatenating files, rearranging columns, dropping duplicates, and generating master files with optional, custom columns for VeDDRA category analysis.

---

### ✉️ Contact  

If you have questions/concerns, contact [openadverseevents@gmail.com](mailto:openadverseevents@gmail.com). 

# Cramerton RECDESK Address Cleaning Project

This project focuses on cleaning and standardizing address data for Cramerton, NC. It processes address records from Cramerton_Parcels.csv to create a standardized address format for RECDESK integration.

## Project Structure
```
Cramerton_RECDESK_Cleaning/
├── data/                    # Contains all CSV files
│   ├── Cramerton_Parcels.csv    # Original parcel data
│   ├── ETJ_IDS.csv             # ETJ parcel IDs to exclude
│   ├── Cramerton_Final.csv     # Final cleaned address data
│   └── Removed_Records.csv     # Records removed during cleaning
├── Cleaning.ipynb             # Main cleaning script
└── README.md                  # Project documentation
```

## Data Processing Steps

1. **Initial Data Loading**
   - Loads Cramerton_Parcels.csv
   - Removes ETJ parcels using ETJ_IDS.csv
   - Cleans empty and whitespace-only addresses

2. **Address Standardization**
   - Standardizes special street names:
     - "S NEW HOPE RD" → "SOUTH NEW HOPE RD"
     - "N MAIN ST" → "NORTH MAIN ST"
     - "S MAIN ST" → "SOUTH MAIN ST"
   - Preserves house numbers for South New Hope Road addresses

3. **Residential Street Processing**
   - Identifies and processes residential streets
   - Creates standardized records for numbered streets (First through Eighteenth)
   - Maintains correct city, state, and zip code information

4. **Output Generation**
   - Creates Cramerton_Final.csv with standardized addresses
   - Generates Removed_Records.csv for review
   - Sets appropriate ValidationType ('S' for residential streets, 'E' for exact matches)

## Address Validation Types
- 'S': Residential streets (standardized)
- 'E': Exact match addresses

## City/State/Zip Information
- Cramerton, NC 28032 (default)
- Belmont, NC 28012 (for specific streets)
- Gastonia, NC 28056 (for South New Hope Road)

## Usage
1. Place input CSV files in the data folder
2. Run Cleaning.ipynb
3. Review output files in the data folder
4. Use Cramerton_Final.csv for RECDESK integration

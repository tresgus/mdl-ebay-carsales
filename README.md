# eBay Used Car Listings: Data Cleaning and Exploration

A Jupyter notebook that cleans and explores 50,000 used car listings from *eBay Kleinanzeigen*, the classifieds section of the German eBay website.

## Data

`Data/autos.csv` is a sample of 50,000 listings crawled in March and April 2016. The original dataset is available on [Kaggle](https://www.kaggle.com/datasets/sijovm/used-cars-data-from-ebay-kleinanzeigen).

The file is Latin-1 encoded, so it is read with `encoding="latin1"`.

Each row is one listing, with columns that include the price, brand, model, vehicle type, registration year, odometer reading, fuel type, gearbox and whether the car has unrepaired damage.

## What the notebook does

**Data cleaning**

- Renames the columns from camelCase to snake_case.
- Drops columns with almost no information (`seller`, `offer_type`, `num_photos`).
- Converts `price` and `odometer` from text (`"$5,000"`, `"150,000km"`) to integers.
- Removes listings with unrealistic prices (outside $1 to $350,000).
- Removes listings with impossible registration years (outside 1930 to 2016).
- Translates German category values to English (`vehicle_type`, `gear_box`, `fuel_type`, `unrepaired_damage`).

**Data exploration**

- Looks at when listings were crawled, created and last seen.
- Compares the mean price of German car brands.

## Key findings

- About 93% of the listings (46,674) remain after cleaning.
- German brands make up about 63% of all listings, and Volkswagen alone accounts for about 21%.
- Porsche is by far the most expensive German brand (mean of about $45,600). Audi, Mercedes-Benz and BMW form a premium tier ($8,300 to $9,300), and Volkswagen sits in the middle at about $5,400. Smart, Opel and Trabant are the cheapest (under $3,600).
- Nearly two thirds of listed cars show the maximum odometer reading of 150,000 km.

## Running the notebook

Requires Python 3 with `pandas`, `numpy` and Jupyter.

```bash
pip install -r requirements.txt
jupyter notebook autos_exploration.ipynb
```

You can also open `autos_exploration.ipynb` in VS Code with the Jupyter extension. Run the notebook from the repository root so the `Data/autos.csv` path resolves.

## Repository structure

```
.
├── Data/
│   └── autos.csv              # 50,000 eBay Kleinanzeigen listings
├── autos_exploration.ipynb    # cleaning and exploration notebook
├── requirements.txt
└── README.md
```

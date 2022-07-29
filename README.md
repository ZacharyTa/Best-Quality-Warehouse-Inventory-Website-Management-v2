# Best-Quality-Warehouse-Inventory-Website-Management-v2

=========Background============
Best Quality Furniture

-Wholesale retail company that offers extensive range of beautiful and magificent furnishings for your household or office

(https://bestqualityfurn.com/)
===============================

=========Purpose===============
- Update the existing product's price and inStock Status on Best Quality Furniture's website using MSAccess
> Match Product Names in Exported Accuterm's CSV file to the Website's Exported Inventory CSV file and update its Price and
inStock Status (Based on how much is in stock and its status(discontinuing vs continuing)

> Generate List of Products to Delete off Website using MSAccess
- Find products that are discontinuing and no longer in stock. Match these Product Names in Exported Accuterm's CSV file to 
Website's Exported Inventory CSV file and generate CSV file "Items To Delete off Website.csv".

- Generate List of Products to Add onto Website using MSAccess
> Find products that are on Accuterm and either: Continuing or Discontinuing(Only if in Stock). Match these Product Names in 
Exported Accuterm's CSV file to Website's Exported Inventory CSV file and generate CSV file "Items To Add onto
Website.csv", if match isn't found.
- (NOTE: Some items may be added here because of incorrect names on the website's end)

> Generate List of Products in Accuterm that encountered runtime error
- If a program throws an invalid_argument error, it will generate a CSV file "Accuterm Items with Error Naming Conventions.csv"
(Usually due to commas in discriptions, which causes the code to read into incorrect columns)
===============================

===== HOW TO USE ==========
- Inputs Outside of this Github Page:
> Accuterm's Exported Data as CSV files -> "running.csv" + "s2.csv" + "s3.csv" + "s4.csv"
>
> WordPress's Exported Inventory as CSV File (w/ WooCommerce) -> "Website Inventory.csv"
> 
> (NOTE: These CSV files must be named exactly as shown)

- MSAccess Setup
> External Data > New Data Source > From File > Text File
> 
> Import Accuterm's and Wordpress's Exported csv files into new table in the current database (Ex. "running.csv")
> 
> Delimited > Comma + First Row Contains Field Names + Indexed(Yes, No Duplicates > Choose own Primary Key (Accuterm csv files: Product ID, Wordpress csv files: Prod ID
> 
> Create Queries
>> Query one

> Outputs: 
- CSV files-> "Items To Delete off Website.csv" + "Items To Add onto Website.csv" + "Accuterm Items with Error Naming Conventions.csv" + "Updated Website Inventory.csv"
===============================

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

- MSAccess Importing Tables Setup
> External Data > New Data Source > From File > Text File
> 
> Import Accuterm's and Wordpress's Exported csv files into new table in the current database (Ex. "running.csv")
> 
> Delimited > Comma + First Row Contains Field Names + Indexed(Yes, No Duplicates > Choose own Primary Key (Accuterm csv files: "Product ID", Wordpress csv files: "ID"
> 
- MSAccess Queries Setup
> Create > Query Design > Select > SQL View (Bottom right) > Copy + Paste SQL Code from "MSAccess SQL Queries Setup" in Github > Save as "(Name of the Queries.txt files -> Ex."AddItemsToWebsite")
>
> (NOTE: These Queries must be named exactly as shown in the "MSAccess SQL Queries Setup" folder)

- Query Results Interpretation: 
> AddItemsToWebsite: Lists valid/sellable items on Accuterm that is not on the Website yet
>
> Import to Website: Updates/Writes Website Items' In Stock/Regular price status in a specific format that can easily be exported and directly imported into the website's inventory via Wordpress's Woocommerce Product Import Plugin
>
> RemoveDiscontItems: Lists Discontinuing website items that are: no longer in stock or contain a nonvalid price value (Ex. <$3)
>
- Website Inventory Not in AllItemsNormalized: Lists website items that do not match with any valid/sellable items on Accuterm, which could the result of: Website Naming Error or Removal of Accuterm Item
>
> AllItemsNormalized: Lists all valid/sellable items on Accuterm (Ex. Subitems like Dressers/Nightstands are not valid/sellable while Beds/Bedroom Sets/Chairs are)
>
> ContItemsNormalized: Lists all Continuing valid/sellable items on Accuterm that are runnning(running)/slow selling(s2)
>
> DiscontItemsNormalized: Lists all Discontinuing valid/sellable items on Accuterm that are discontinued(s3)/closed out(s4)
>
> InStock?: Lists all valid/selleable items and Creates/Writes a boolean value to another field, "In stock", that represents its In Stock status on the website
>
> Regular Price: Lists all valid/selleable items and Creates/Writes an integer value to another field, "Regular price", that represents its selling price on the website
===============================

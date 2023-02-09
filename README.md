# Nashville_Housing
Home value data for the Nashville market.

The code performs several operations on the table to standardize and clean the data. First, the "SaleDate" field is converted to a standardized date format, and a new column "SaleDateConverted" is created to store these dates.

Next, the "PropertyAddress" field is populated using the ISNULL function and by joining the table with itself. This ensures that all the property addresses are complete.
The "OwnerAddress" and "PropertyAddress" fields are then broken out into separate columns for street, city, and state. This makes it easier to analyze the data and perform various operations on it. Then, the code creates five new columns in the "Nashville" table to separate the property address and owner address into "PropertyStreet", "PropertyCity", "OwnerStreet","OwnerCity" and "OwnerState". It uses the REVERSE and PARSENAME functions to extract the street, city, and state from the original property address field and updates the new columns with these values.

After that, the "SoldAsVacant" field is updated to replace "Y" and "N" with "Yes" and "No", respectively. There are two ways to update the values, either with two separate UPDATE statements or with a CASE statement.

Finally, the code removes duplicates from the "Nashville" table. It does this by creating a temporary table(CTE) named "RowNTable" that assigns a row number to each row in the table based on the values in the "ParcelID" and "SaleDateConverted" fields. The code then selects all the rows from the "RowNTable" where the row number is 1, and inserts them into the "Nashville" table. This effectively removes all duplicates from the table.

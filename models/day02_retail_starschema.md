# RetailCo Star Schema — Day 02

## Purpose
Design a star schema for RetailCo sales reporting in Power BI.

## Declared Grain
The Transactions fact table has one row per transaction line item, representing one product line within a transaction. Verify this grain against the official source data.

## Fact Table: Transactions
Expected columns:
- TransactionID
- TransactionDate
- CustomerID
- ProductID
- StoreID
- Quantity
- SalesAmount
- CostAmount
- Profit

## Dimension Tables

### Customers
CustomerID (primary key), CustomerName, CustomerSegment.

### Products
ProductID (primary key), ProductName, Category, Subcategory.

### Stores
StoreID (primary key), StoreName, City, Region.

### Date
Create a calendar table with DAX:

    Date = CALENDARAUTO()

Add Year, Month Number, Month Name, and Quarter. Mark Date as the date table.

### Returns
Connect Returns to Transactions using TransactionID after validating key uniqueness and relationship cardinality.

## Relationships
- Customers[CustomerID] 1-to-many Transactions[CustomerID]
- Products[ProductID] 1-to-many Transactions[ProductID]
- Stores[StoreID] 1-to-many Transactions[StoreID]
- Date[Date] 1-to-many Transactions[TransactionDate]
- Transactions[TransactionID] to Returns[TransactionID], with cardinality verified from source data.

Use appropriate single-direction filtering and avoid ambiguous relationship paths.

## Validation
- Confirm actual source column names and data types.
- Check dimension key uniqueness.
- Validate dates and unmatched keys.
- Reconcile transaction and return counts.
- Verify relationship cardinalities.

## Assumptions
Field names and grain are provisional until the official RetailCo CSV files are inspected.

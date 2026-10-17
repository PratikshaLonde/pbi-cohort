# RetailCo DAX Measures — Day 02

These measures assume the column names described in day02_retail_starschema.md. Verify them against the official RetailCo data before implementation.

## Total Sales

    Total Sales = SUM(Transactions[SalesAmount])

## Total Quantity

    Total Quantity = SUM(Transactions[Quantity])

## Total Profit

    Total Profit = SUM(Transactions[Profit])

## Total Cost

    Total Cost = SUM(Transactions[CostAmount])

## Sales for Selected Year

    Sales Selected Year =
    CALCULATE(
        [Total Sales],
        'Date'[Year] = SELECTEDVALUE('Date'[Year])
    )

## Returned Transaction Count

    Returned Transaction Count =
    CALCULATE(
        DISTINCTCOUNT(Returns[TransactionID])
    )

## Profit Margin

    Profit Margin =
    DIVIDE([Total Profit], [Total Sales], 0)

## Average Sales per Transaction

    Average Sales per Transaction =
    DIVIDE(
        [Total Sales],
        DISTINCTCOUNT(Transactions[TransactionID]),
        0
    )

## Validation Notes

- Confirm all referenced columns exist.
- Verify whether TransactionID identifies a transaction or transaction line.
- Validate return counts against the Returns table grain.
- Format sales and profit as currency and Profit Margin as a percentage.
- Test measures with date, product, store, and customer filters.

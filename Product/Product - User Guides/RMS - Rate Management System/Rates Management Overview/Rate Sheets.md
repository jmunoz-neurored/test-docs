# Rate Sheets

---

## Definition

Rate Sheets are customer-specific price lists. They group finalized selling prices and can be shared directly with customers. Rate Sheets have start and end validity dates, a lifecycle status, and support approval workflows—allowing closer collaboration with customer procurement teams. Each Rate Sheet contains multiple **Rate Sheet Lines**, which store individual rate entries.

## Uses

Use Rate Sheets to:

* Share custom pricing with customers
* Apply bulk customer discounts
* Enable fast and accurate quoting using customer-specific prices

Rate Sheets provide a structured way to manage customer-facing prices based on pre-negotiated carrier rates and internal markups.

## Prerequisites

Before creating a Rate Sheet, ensure the following components are configured:

* **Customer Account**: The account must be created and available to associate with the Rate Sheet.
* **Rates**: Base carrier rates must be uploaded via Rate Contracts. These serve as the foundation for Rate Sheet pricing.
* **Rate Books**: Must be set up with applicable markups. Rate Sheets use Rate Books to derive list prices.

## Structure

```mermaidjs
classDiagram
    Rate Sheet"1" -- "n" Rate Sheet Line
    Rate Sheet Line"n" -- "1" Rate Book Line
    Rate Sheet Line "n" -- "1" Rate Revision
    Rate Book Line "n" -- "1" Rate
    Rate Revision "n" -- "1" Rate
```

To manage customer dedicated prices we have two Rate Sheet related business objects:

* **Rate Sheet**: A container for a set of customer-specific rates. It includes status and validity fields and can be configured for a single customer or used as a generic template. Users can view all related Rate Sheet Lines through a dedicated interface.
* **Rate Sheet Line**: Represents the final customer-facing price for a specific service. It references a **Rate Revision** (carrier cost) and a **Rate Book Line** (list price), and stores the final price, currency, and validity. Discounts can be applied globally or line-by-line.

## Integration

| Module | Integration Type |
|----|----|
| Rates | Source data for Rate Sheet Lines. Each line connects to a **Rate Revision** (carrier price) and a **Rate Book Line** (list price). |
| Quotes | Quotes pull pricing from Rate Sheet Lines during rate searches in the Pricing Control Tower. |


\
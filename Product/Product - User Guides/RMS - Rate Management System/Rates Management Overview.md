# Rates Management Overview

---

## Definitions

Pricing in logistics is complex. Rates usually present high variability. The attributes that can vary between different rates can be: route, type (freight, warehouse services, storage, surcharges, etc.), unit of measurement (uom), container type (cargo transport unit). Some rates might be dependent on other rates. For instance, when a surcharge is associated with a specific freight rate.

Because of this complexity, we make use of different business objects that allow to efficiently store and maintain big amounts of rates.

* **Charge code**: master data object that defines a type of service. Can be freight, surcharge,
* **Rate**: stores all the qualitative defining attributes of rate, including route, origin, destination, charge code, price unit of measurement (uom), cargo transport unit (container type)
* **Rate Contract:** represents an ongoing framework with a specific carrier with a custom spreadsheet template. It will have Rate Contract Revisions for each new set of rates that you upload to the system.
* **Rate Book**: serves as a group of rates to be used for customer tiers. It allows to add markups to the carrier rates.
* **Rate Sheet:** allows to create customer specific rates with custom pricing.

## Overview

These objects (Rate, Rate Contract, Rate Book and Rate Sheet) are related between each other. An outline of the standard data workflow can be seen below:

```mermaidjs
sequenceDiagram
    autonumber
    participant CR as Carrier Rates
    participant RC as Rate Contract
    participant RB as Rate Book
    participant RS as Rate Sheet
    CR->>RC: Upload rates
    note right of CR: Uploaded using a predefined<br/>template via email or app 
    RB->>RC: Fetch Carrier Rates
    note right of RC: Group rates by region,<br/>service level or other<br/>criteria and apply markups.
    RS->> RB: Apply dedicated discounts<br/>for customers
```
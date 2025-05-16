# Quoting

---

## Definitions

Quoting in Neurored is based on the Transport Quote object. Transport Quotes are used to record a spot quotation requested by a customer to move cargo from one geography to another. Transport Quotes support the data needed for one transport leg.

In the future there will be an overlayed structure to allow for multi-stop quotations with pricing options from different carriers.

## Overview

The process to create a Transport Quote is outlined in the diagram below:

```mermaidjs
sequenceDiagram
    autonumber
    participant C as Customer
    participant S as Salesperson
    participant PCT as Pricing Control Tower
    participant RS as Rate Sheets
    participant A as API

    C->>S: Requests pricing
    note right of C: Sends Transport Details via email<br/>or creates record in dedicated portal
    S->>PCT: Inputs Transport Details<br/>in guided workflow
    note right of S: Necessary data includes: customer, origin,<br/>destination, mode of transport, service level<br/>and cargo details. 
    par 
        PCT->>RS: Gets rates via internal Interface
    and
        PCT->>A: Gets rates from external suppliers
    end
    S->>C: Sends Transport Quote with <br/>pricing details via email<br/> or customer portal
```
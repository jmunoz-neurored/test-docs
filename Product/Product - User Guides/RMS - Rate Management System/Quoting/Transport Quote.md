# Transport Quote

---

## Definition

A Transport Quote is a business object where spot transportation requests for a specific service can be recorded. Transport Quotes help streamline the process to log in the transportation details and the cargo, and to retrieve rates from the Rates Management System and add them to it. Transport Quotes allow the creation of custom documents to share with the customer listing all the necessary details and terms for proper contract management.

## Prerequisites

Before creating a quote there are several data points that need to be created:

* **Cargo Transport Units**: can be either conteiners or pallets, cases, crates, etc.
* **Charge Codes**: regardless of the use of predefined rates, charge codes must be set up to be able to add fees to the quote
* **Geographical Data**: at least Countries and Locations must be set up (done during onboarding)

Some additional data can be reused from the database or can be setup during quote creation:

* **Accounts**: several accounts can be added to the Transport Quote, such as the Customer (mandatory), Shipper, Consignee, Carrier, Origin Agent, Destination Agent, Land Carrier and Customs Broker.
* **Contacts**: contacts belonging to the above mentioned accounts can be added during the quoting process
* **Rates**: if you want to use stored rates in the system you must first set up your Rate Contracts, Rate Books and Rate Sheets

## Structure

Transport Quotes have a layered architecture to allow for the flexibility needed to process all the modes of transport:

```mermaidjs
classDiagram
    Account"1" -- "n" Transport Quote
    TransportQuote "1" -- "n" Transport Quote Cargo
    Transport Quote Cargo "n" -- "1" Cargo Transport Unit
    Transport Quote "1" -- "n" Transport Quote Fee
    Transport Quote Fee "n" -- "1" Charge Code
```

## Integration

| Module | Integration Type |
|----|----|
| Rates | Transport Quotes allow you to search for rates from the Rates Management System to strealine quoting process. |
| Order Management | Transport Quotes allow you to create Transport Orders automatically leveraging all the data already inputted in the quoting process. |
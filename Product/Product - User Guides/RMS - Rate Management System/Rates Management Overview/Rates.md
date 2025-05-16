# Rates

---

## Definition

Rates are the core pricing records that define the details of a logistics service, including origin, destination, transport mode, service type, price unit, and container type. Each Rate represents a unique service definition and is associated with a Charge Code. Rate Contracts group these Rates and manage their lifecycle through periodic Rate Revisions. While Rates define the structure of a service, Rate Revisions provide the time-bound commercial terms (e.g., price, currency, and validity) tied to that service ([more here](https://outline.dev.neurored.com./Rate%20Contracts.md)).

## Structure

Rates store the main details and definition items of a given service:

* **Geography**: rates can be configured at different geographic levels. They can be configured for a preconfigured *Route* or for a non-exclusive combination of *Origin Country*, *Origin Zone*, *Destination Country* and *Destination Zone* (more on geographical definitions below)
* **Rate Type**: helps categorize rates in freight, pickup, origin, destination, surcharge and other.
* **Price Type**: indicates the unit of measure (UOM) used for pricing (per kg, per mile/km, per container, per hour, per TON, per pallet, etc.)
* **Transport Mode**: describe the mode of transport of the service (air, sea, road, rail or multimodal)
* **Cargo Transport Unit**: specifies the container type (if applicable), using standard CTU codes.

> **Note**: Rate Type and Transport Mode can be inherited from the Charge Code or explicitly defined in the rate.

The rates are related with multiple business objects:

```mermaidjs
erDiagram
    Rate }o--|| "Charge Code": has
    Rate }o--|| "Cargo Transport Unit" : has
    Rate }o--o| Zone: Origin
    Rate }o--o| Zone: Destination
    Rate }o--o| Country: Origin
    Rate }o--o| Country: Destination
```

Rates are typically managed within the structure of a **Rate Contract**, which serves as the container for one or more Rate Contract Revisions and their associated Rate Revisions.

For additional context on how rates are used within rate contracts, see the **[Rate Contracts](https://outline.dev.neurored.com./Rate%20Contracts.md)** documentation.

## Prerequisites

Before uploading or managing rates, ensure the following components are preconfigured:

* **Charge codes**: define the type of service and must be created before rates. Each rate must reference exactly one charge code.
* **Cargo Transport Units**: standardize container types with predefined CTU codes.
* **Geographical Data**: ensure all Countries and Locations are configured. Zones can be created dynamically during rate upload.

## Integration

| Module | Integration Type |
|----|----|
| Rate Contracts | Rates are the base definition for pricing updates in Rate Contract Revisions. ([more here](https://outline.dev.neurored.com./Rate%20Contracts.md)) |
| Rate Books | Rates are the base definition of list prices stored in Rate Book Lines. ([more here](https://outline.dev.neurored.com./Rate%20Books.md)) |
| Rate Sheets | Rates are the base definition of customer prices stored in Rate Sheet Lines. ([more here](https://outline.dev.neurored.com./Rate%20Sheets.md)) |
| Quoting | The Pricing engine uses the rate details as part of its query when searching for rates for a specific service. ([more here](https://outline.dev.neurored.com./../Quoting.md)) |
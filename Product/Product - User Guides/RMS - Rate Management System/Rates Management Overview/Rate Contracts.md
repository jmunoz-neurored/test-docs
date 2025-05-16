# Rate Contracts

---

## Definition

Rate Contracts are master records that group together rates provided by a carrier for either ongoing or spot pricing agreements. Rate Contracts are the primary entry point for uploading carrier rates into the system. Each upload must be associated with a Rate Contract to logically organize and version the rates.

## Uses

You can upload rates into the system using a Rate Contract in two main scenarios:

* **New Rate Contract**: Use when no prior contract exists for the selected template. You will need to define the owner account, carrier, and relevant metadata during setup.
* **Existing Rate Contract**: Use when updating or appending rates to an existing agreement. This ensures pricing continuity and proper version control.

## Prerequisites

Before using Rate Contracts, ensure the following data is configured:

* **Owner Account**: Define the account responsible for the contract. This controls visibility and access.
* **Carrier Account**: If the contract is tied to a specific carrier, the carrier's external ID must be available for rate mapping.
* **Charge Codes**: Each uploaded rate must reference a single charge code. The charge code determines the service type and must be aligned with services configured in the ERP.

## Structure

Rate Contracts are designed for flexibility and version control. They support periodic price updates while maintaining a historical record of rate changes.

```mermaidjs
classDiagram
    class Rate Contract
    class Rate Contract Revision
    class Rate
    class Rate Revision
    class Carrier
    class Charge Code
    class Account
    Rate Contract "1" -- "n" Rate Contract Revision
    Rate Contract Revision "1" -- "n" Rate Revision
    Account "1" -- "n" Rate Contract
    Carrier "0..1" -- "n" Rate Contract
    Rate Revision "n" -- "1" Rate
    Rate "n" -- "1" Charge Code
```

As per the diagram, there are several business objects involved in the configuration and usage of carrier rates in the Rates Management System:

* **Rate Contracts**: Groups together related rates for a carrier. The contract is owned by an Account, which could represent an internal office, agent, or external carrier. A Rate Contract can include rates from multiple carriers but typically represents a single agreement.
* **Rate Contract Revision**: Represents a batch upload of rate updates under a contract. Each revision includes metadata like validity dates, number of rows processed, AWS file ID, and status. You can manage all Rate Revisions from a dedicated tab.
* **Rate Revision**: Represents a specific pricing version of a Rate. It includes granular attributes such as price, currency, transit time, free days, minimum price, and exemptions. The underlying Rate provides the broader service definition (e.g., route, mode, price type).
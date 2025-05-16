# Rate Books

---

## Definition

Rate Books are pricing templates used to group rates from multiple carriers and Rate Contracts. They allow you to manage and standardize pricing strategies across customer segments. Use Rate Books to apply markup rules in bulk and generate list prices derived from carrier costs. Rate Books are dynamic: they automatically reflect the latest Rate Revision for each rate.

## Uses

Use Rate Books to:

* Group rates by customer segment or sales region
* Apply markup policies (percentage or fixed amount) to carrier rates
* Provide list prices to customer-facing tools and quoting processes
* Share standardized pricing sets with commercial teams or customers
* Enforce pricing consistency through business rule templates

## Prerequisites

Before creating a Rate Book, you must:

* Upload rates via the **Rate Contract** process
* Ensure **Rate Revisions** exist for each rate, as these define the base (carrier) prices
* Configure any required markup policies

Rate Books rely on existing Rates and Rate Revisions to function properly.

## Structure

Rate Books are structured in a way that allows you to have Rates in multiple Rate Books. Rate Books will include a set of rates that belong together for sales and quoting processes.  Rate Books act as a template for rates for your customers, they automatically update their price based on the latest Rate Contract version and the specified markup. Rate Books are not directly tied to Rate Revisions, but to Rates, so that it is tied to the latest version automatically.

```mermaidjs
classDiagram
    class Rate Book
    Rate Book "1" -- "n" Rate Book Line
    Rate Book Line"n" -- "1" Rate
```

Rate Book management includes two main business object and the relationship with the Rate:

* **Rate Book**: A container that groups Rate Book Lines. It includes a name, description, markup type (percentage or fixed), and default markup value. Rate Book Lines inherit this markup unless explicitly overridden. Each Rate Book supports a dedicated interface to manage its lines.
* **Rate Book Line**: Represents a priced version of a Rate within a Rate Book. Each line references a **Rate** and inherits the latest **Rate Revision** to determine the base price. It can apply the default Rate Book markup or a line-specific override.
* **Rate**: The base pricing object, linked to charge codes, geographies, container types, and other rate definition items. Rate Books always reference the **latest valid Rate Revision** of each Rate to ensure prices remain up to date.
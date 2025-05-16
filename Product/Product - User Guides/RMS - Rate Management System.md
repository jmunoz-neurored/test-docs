# RMS - Rate Management System

## Overview

Pricing in Neurored is managed in the Rates Management System (RMS). The Rates Management System allows you to manage carrier rates, customer rates and customer quotes. It is designed to allow for scalability and performance when dealing with vast amounts of rates with varying structures and attributes.

## Uses

The RMS is an app that allows you to:

* Upload carrier rates from predefined spreadsheet templates and store them in the cloud
* Create, store and query service rates for transportation, warehousing, value-added services or any other service that occurs in the supply chain.
* Organize, group and maintain those service rates in rate books to apply mass markup fees for different customer tiers
* Create dedicated Rate Sheets from Rates to apply discounts or special conditions to specific customers
* Create Customer Quotes for any given route, mode of transport, service type (FCL, LCL, Air, etc.), Incoterm
* Price Customer Quotes from rates stored in Rate Books and Rate Sheets
* Send Customer Quotes to customers via email using predefined document templates

## Integration

The Neurored RMS is integrated with the following other Neurored components:

| Module | Integration Type |
|----|----|
| Master Data | You must setup Accounts and Charge Codes before setting up Rates and creating Transport Quotes. |
| TMS | You can create Transport Orders from Transport Quotes |

## Features

* **Quoting**: you can create and manage spot quotes or multi-route quotes for your customers with the quoting module.
* **Rates Management:** manage pricing and rates including your carrier rates, customer rate books and customer rate sheets
# Configuration

Lorem ipsum

## Implement Fulfillment Data Source

Lorem ipsum Supports S3 as an input source Create named credential Remote settings for AWS Same input source can be used for connections Basically access to the data lake created by airbyte ELT processes

## Implement Neurored WMS Fulfillment Integration

Custom Setting: Customer Connection Neurored WMS Setting: defaultWarehouse

## Fulfilment Integration Architecture

Fulfillment Client Order Source (e.g. Shopify Order Stream) Connected App Named Credentials Platform Event (service class, trigger subscriber, platformEventSubscriberConfig, Profile(external credentials access)) Integration Setting Custom Metadata Type Airbyte ELT (connections, source, destination, webhook notification, scheduling) AWS S3 Data Lake AWS Virtual Private Cloud (VPC, EC2, API Gateway, Lambda, Secrets Manager) Permissions CORE Requirements(Exceptions, Logging, Constants, Configuration, Integration)
# Hublink Reseller REST API

This is the documentation for the public API for resellers of [CMYKhub](https://www.cmykhub.com) products.

Hublink is the system used for generating quotes and 
prices on printed products. This API can be used to 
get prices, place orders and get order status information. 

## Authentication
All requests must include reseller ID and api key headers.
EG
```HTTP
ResellerID: 9876
ApiKey: aBcDeFg1234
```

## Links
Each resource contains a property named "Links". This is an array of links to related resources.
These are highly preferred over hard-coded urls as urls may change between versions.
Starting at the base address of (https://hublink.api.cmykhub.com) discovery of urls is possible
to all other resources in the API. 

## SDK's
* [Dotnet Api Client](https://github.com/CMYKhub/Reseller-NET-SDK)
* [REST API Reference](Api%20Reference.md)

## Contact

For questions or errors with the documentation please report an [issue](https://github.com/CMYKhub/Reseller-NET-SDK/issues/new)

For API access please [contact your local representeative](https://www.cmykhub.com/locations.html).

For reseller enquiries please [register at CMYKhub](https://www.cmykhub.com/register.php)
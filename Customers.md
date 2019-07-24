# Customers

<span style="color: blue">**GetCustomersAsync**</span>
<br/>
<span style="color: blue">**GetCustomerAsync**</span>

Returns customers for the reseller specified by the ResellerID header.

Customers can be filtered by customerId to return a single customer.

Eg .Net C# request to get all customers
```csharp
	public async Task<IEnumerable<Customer>> GetCustomers()
	{
		return await ManufacturingClient.GetCustomersAsync();
	}
```
Eg .Net C# request to get customer from customer id
```csharp
	public async Task<Customer> GetCustomer(string id)
	{
		return await ManufacturingClient.GetCustomerAsync(id);
	}
```

Json Response
```json
{
    "CustomerId": "4306",
    "Name": " Lorum Ipsum ",
    "ContactName": "",
    "Address": {
        "State": {
            "Name": "Unknown",
            "Abbreviation": "UNK",
            "CountryCode": "AU"
        },
        "Country": {
            "Code": "AU",
            "Name": "Australia",
            "Iso2Digit": null,
            "Iso3Digit": null,
            "CallingCode": null
        },
        "Address1": "",
        "Address2": "",
        "City": "",
        "Postcode": "0"
    },
    "ContactMethods": {},
    "Links": [
        {
            "Uri": "http://localhost:50595/man/Customers/1511837c-9d1f-406e-a9a3-e18f0c64de0a",
            "Relation": "self",
            "MediaType": "application/vnd.cmykhub+json"
        },
        {
            "Uri": "http://localhost:50595/man/Customers/1511837c-9d1f-406e-a9a3-e18f0c64de0a/DeliveryAddresses",
            "Relation": "http://schemas.cmykhub.com/api/customers/relations/delivery",
            "MediaType": "application/vnd.cmykhub+json"
        }
    ]
}
```

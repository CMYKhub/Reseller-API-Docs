# Customers

<span style="color: blue">**GET**</span> /man/customers

Returns customers for the reseller specified by the ResellerID header.

Customers can be filtered by customerId to return a single customer.

Eg
Javascript ajax request
```javascript
    $.ajax({
      url: "/man/customers",
      dataType: "json",
      type : "GET",
      data: {
          customerId: "4306"
      },
      success : function(r) {
        console.log(r);
      }
    });
```
Response
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

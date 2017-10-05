# Products


<span style="color: blue">**GET**</span> /man/products

Returns standard products optionally filtered by name.

Eg
Javascript ajax request
```javascript
    $.ajax({
      url: "/man/products",
      dataType: "json",
      type : "GET",
      data: {
          name: "gloss"
      },
      success : function(r) {
        console.log(r);
      }
    });
```
Response
```json
{
    "Items": [
        {
            "Id": "285",
            "Name": "A1",
            "Description": "250gsm Gloss Print 2 Side A1",
            "Code": null,
            "ProductGroup": {
                "Id": "39",
                "Name": "250gsm Gloss Print 2 Side"
            },
            "Links": [
                {
                    "Uri": "http://localhost:50595/man/Products/285",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        },
        {
            "Id": "1868",
            "Name": "A3 Printed 2 side on 170gsm gloss art",
            "Description": "Digital Poster A3 Printed 2 side on 170gsm gloss art",
            "Code": null,
            "ProductGroup": {
                "Id": "149",
                "Name": "Digital Poster"
            },
            "Links": [
                {
                    "Uri": "http://tempuri.org/man/Products/1868",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        },
        {
            "Id": "206",
            "Name": "A4",
            "Description": "170gsm Gloss Print 1 Side A4",
            "Code": null,
            "ProductGroup": {
                "Id": "28",
                "Name": "170gsm Gloss Print 1 Side"
            },
            "Links": [
                {
                    "Uri": "http://tempuri.org/man/Products/206",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        }
    ]
}
```

Javascript ajax request
```javascript
    $.ajax({
      url: "/man/products/206",
      dataType: "json",
      type : "GET",
      success : function(r) {
        console.log(r);
      }
    });
```
Response
```json
{
    "Id": "206",
    "Name": "A4",
    "Description": "170gsm Gloss Print 1 Side A4",
    "Code": null,
    "ProductGroup": {
        "Id": "28",
        "Name": "170gsm Gloss Print 1 Side"
    },
    "Links": [
        {
            "Uri": "http://tempuri.org/man/Products/206",
            "Relation": "self",
            "MediaType": "application/vnd.cmykhub+json"
        }
    ]
}
```

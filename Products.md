# Products


<span style="color: blue">**GET**</span> /man/products

Returns standard products optionally filtered by name.

Eg
Javascript ajax request
```javascript
    $.ajax({
      url: "/man/products?name=gloss",
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
                    "Uri": "http://tempuri.org/man/Products/285",
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




<span style="color: blue">**GET**</span> /man/wideformat/products

Returns wide format products optionally filtered by name.

Eg
Javascript ajax request
```javascript
    $.ajax({
      url: "/man/wideformat/products?name=canvas",
      dataType: "json",
      type : "GET",
      data: {
          name: "canvas"
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
            "Id": "bd69fd35-7860-44b7-9099-e4c9e4fc6aa8",
            "Name": "Canvas Poster 1 Side",
            "Description": "Canvas Poster 1 Side",
            "Code": "bd69fd35-7860-44b7-9099-e4c9e4fc6aa8",
            "ProductGroup": null,
            "Links": [
                {
                    "Uri": "http://tempuri.org/man/WideFormat/Products/bd69fd35-7860-44b7-9099-e4c9e4fc6aa8",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        }
    ],
    "Links": [
        {
            "Uri": "http://tempuri.org/man/WideFormat/Products",
            "Relation": "self",
            "MediaType": "application/vnd.cmykhub+json"
        }
    ]
}
```

Javascript ajax request
```javascript
    $.ajax({
      url: "/man/wideformat/products/bd69fd35-7860-44b7-9099-e4c9e4fc6aa8",
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
    "Id": "bd69fd35-7860-44b7-9099-e4c9e4fc6aa8",
    "Name": "Canvas Poster 1 Side",
    "Description": "Canvas Poster 1 Side",
    "Code": "bd69fd35-7860-44b7-9099-e4c9e4fc6aa8",
    "ProductGroup": null,
    "Links": [
        {
            "Uri": "http://tempuri.org/man/WideFormat/Products/bd69fd35-7860-44b7-9099-e4c9e4fc6aa8",
            "Relation": "self",
            "MediaType": "application/vnd.cmykhub+json"
        }
    ]
}
```

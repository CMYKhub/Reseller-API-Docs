# Hublink Reseller REST API

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


## Paper

<span style="color:blue">**GET**</span> /man/papers

Returns papers optionally filtered by name.

Eg
Javascript ajax request
```javascript
    $.ajax({
      url: "/man/papers",
      dataType: "json",
      type : "GET",
      data: { 
          name: "uncoated"
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
            "Id": "356",
            "Description": "EcoStar Uncoated 100% Recycled  ",
            "Links": [
                {
                    "Uri": "https://hublink.api.cmykhub.com/man/Papers/356",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        },
        {
            "Id": "357",
            "Description": "EcoStar Uncoated 100% Recycled  ",
            "Links": [
                {
                    "Uri": "https://hublink.api.cmykhub.com/man/Papers/357",
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
      url: "/man/papers/356",
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
    "Id": "356",
    "Description": "EcoStar Uncoated 100% Recycled  ",
    "Family": "EcoStar Uncoated 100% Recycled",
    "Colour": "",
    "Texture": "",
    "Weight": 100,
    "Links": [
        {
            "Uri": "https://hublink.api.cmykhub.com/man/Papers/356",
            "Relation": "self",
            "MediaType": "application/vnd.cmykhub+json"
        }
    ]
}
```

## Finishing

<span style="color:blue">**GET**</span> /finishing

Returns finishings optionally filtered by name.

Eg
Javascript ajax request
```javascript
    $.ajax({
      url: "/man/finishings",
      dataType: "json",
      type : "GET",
      data: { 
          name: "fold"
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
            "Id": "85",
            "Name": "Double gate fold 8pp A4",
            "Links": [
                {
                    "Uri": "https://hublink.api.cmykhub.com/man/Finishings/85",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        },
        {
            "Id": "45",
            "Name": "Fold - 10pp DL Concertina (no scoring)",
            "Links": [
                {
                    "Uri": "https://hublink.api.cmykhub.com/man/Finishings/45",
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
      url: "/man/finishings/85",
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
    "Id": "85",
    "Name": "Double gate fold 8pp A4",
    "Description": "",
    "Type": {
        "Id": "0",
        "Name": "SingleItemSheet"
    },
    "Links": [
        {
            "Uri": "https://hublink.api.cmykhub.com/man/Finishings/85",
            "Relation": "self",
            "MediaType": "application/vnd.cmykhub+json"
        }
    ]
}
```

## Finishing/Available

<span style="color:blue">**GET**</span> /finishing/available

Returns finishings available for a given specification.

*width:* The width of the trimmed product in millimetres.

*height:* The height of the trimmed product in millimetres.

*paperWeight:* The weight of the paper in gsm.

*printType:* The type of printing (1=Offset, 2=Digital, 
3=Offset OR Digital).

*book.pp:* The number of printed pages in the book. 
NB if any book parameters are specified then all 
book parameters must be specified.

*book.orientation:* The orientation of the book 
(0=Portrait, 1=Landscape). 
NB if any book parameters are specified then all 
book parameters must be specified.


Eg
Javascript ajax request
```javascript
    $.ajax({
      url: "/man/finishings",
      dataType: "json",
      type : "GET",
      data: { 
          width: 210,
          height: 297,
          paperWeight: 150,
          printType: 1
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
            "Id": "2",
            "Name": "Fold - Roll fold A4 to DL",
            "Links": [
                {
                    "Uri": "https://hublink.api.cmykhub.com/man/Finishings/2",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        },
        {
            "Id": "4",
            "Name": "Fold - Single fold in half",
            "Links": [
                {
                    "Uri": "https://hublink.api.cmykhub.com/man/Finishings/4",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        },
        {
            "Id": "6",
            "Name": "Fold - 6pp DL Roll Fold (Outer-98/99/100mm, Inner-100/99/98mm)",
            "Links": [
                {
                    "Uri": "https://hublink.api.cmykhub.com/man/Finishings/6",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        }
    ]
}
```

**For booklet finishing:**

Javascript ajax request
```javascript
    $.ajax({
      url: "/man/finishings",
      dataType: "json",
      type : "GET",
      data: { 
          width: 210,
          height: 297,
          paperWeight: 150,
          printType: 1,
          book:{
            pp: 32,
            orientation: 0
            }
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
            "Id": "1",
            "Name": "Saddle Staple",
            "Links": [
                {
                    "Uri": "https://hublink.api.cmykhub.com/man/Finishings/1",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        },
        {
            "Id": "86",
            "Name": "Perfect Bind",
            "Links": [
                {
                    "Uri": "https://hublink.api.cmykhub.com/man/Finishings/86",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        },
        {
            "Id": "129",
            "Name": "Wire Bind",
            "Links": [
                {
                    "Uri": "https://hublink.api.cmykhub.com/man/Finishings/129",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        }
    ]
}
```

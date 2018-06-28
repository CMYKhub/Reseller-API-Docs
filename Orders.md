# Orders


<span style="color: blue">**GET**</span> /man/orders

Returns orders for the reseller specified by the ResellerID header.

Orders can be filtered by orderId to return a single order.

Eg
Javascript ajax request
```javascript
    $.ajax({
      url: "/man/orders",
      dataType: "json",
      type : "GET",
      data: {
          orderId: "139424"
      },
      success : function(r) {
        console.log(r);
      }
    });
```
Response
```json
{
    "OrderId": "139424",
    "DateOrdered": "2012-03-10T16:20:59.003Z",
    "DateEstimatedDispatch": null,
    "DateCompleted": null,
    "StatusName": "Cancelled",
    "OrderNumber": "139424",
    "CustomerOrderRef": "",
    "Quantity": 2500,
    "Description": null,
    "PaperTypeDescription": null,
    "ResellerId": null,
    "DeliveryType": {
        "DeliveryTypeID": 0,
        "Name": "ToCentre"
    },
    "DeliveryNote": null,
    "Price": null,
    "QuoteId": "299363",
    "ResellerSamples": false,
    "Links": [
        {
            "Uri": "https://hublink.api.cmykhub.com/man/orders/139424",
            "Relation": "self",
            "MediaType": "application/vnd.cmykhub+json"
        },
        {
            "Uri": "https://hublink.api.cmykhub.com/accounts/payments?orderId=139424",
            "Relation": "http://schemas.cmykhub.com/api/orders/relations/payment",
            "MediaType": "text/html"
        },
        {
            "Uri": "https://hublink.api.cmykhub.com/pp/orders?orderId=139424",
            "Relation": "http://schemas.cmykhub.com/api/prepress/relations/orders/artwork",
            "MediaType": "application/vnd.cmykhub+json"
        }
    ]
}
```





<span style="color: blue">**POST**</span> /man/orders

Creates an order for print.

## Existing Quote
Orders can be placed with reference to an existing quote.

Eg
Javascript ajax request
```javascript
    $.ajax({
      url: "/man/orders",
      dataType: "json",
      type : "POST",
      data: {
          quoteId: "98765"
      },
      success : function(r) {
        console.log(r);
      }
    });
```
Response
```json
{
    "OrderId": "139424",
    "ResellerId": 9999,
    "Links": [
        {
            "Uri": "https://hublink.api.cmykhub.com/man/orders/139424",
            "Relation": "self",
            "MediaType": "application/vnd.cmykhub+json"
        },
        {
            "Uri": "https://hublink.api.cmykhub.com/accounts/payments?orderId=139424",
            "Relation": "http://schemas.cmykhub.com/api/orders/relations/payment",
            "MediaType": "text/html"
        },
        {
            "Uri": "https://hublink.api.cmykhub.com/pp/orders?orderId=139424",
            "Relation": "http://schemas.cmykhub.com/api/prepress/relations/orders/artwork",
            "MediaType": "application/vnd.cmykhub+json"
        }
    ]
}
```

## Previous Product Price
Orders can be placed with reference to a price generated previously.

Eg
Javascript ajax request
```javascript
    $.ajax({
      url: "/man/orders",
      dataType: "json",
      type : "POST",
      data: {
          token: "56dfs6789df6789gdf8769",
          reference: "MYREF: 653",
          notes: "Logo Colour A26"
      },
      success : function(r) {
        console.log(r);
      }
    });
```
Response
```json
{
    "OrderId": "139424",
    "ResellerId": 9999,
    "Links": [
        {
            "Uri": "https://hublink.api.cmykhub.com/man/orders/139424",
            "Relation": "self",
            "MediaType": "application/vnd.cmykhub+json"
        },
        {
            "Uri": "https://hublink.api.cmykhub.com/accounts/payments?orderId=139424",
            "Relation": "http://schemas.cmykhub.com/api/orders/relations/payment",
            "MediaType": "text/html"
        },
        {
            "Uri": "https://hublink.api.cmykhub.com/pp/orders?orderId=139424",
            "Relation": "http://schemas.cmykhub.com/api/prepress/relations/orders/artwork",
            "MediaType": "application/vnd.cmykhub+json"
        }
    ]
}
```

## From Product Specification
Orders can be placed with product specification.

Eg
Javascript ajax request
```javascript
    $.ajax({
      url: "/man/orders",
      dataType: "json",
      type : "POST",
      data: {
          product: {
              quantity: 1000,
              orientation: 0,
              finishedSize: { width: 205, height: 280 },
              bindingId: "1",
              printType: 2,
              body:{
              	paperId: "215",
              	pp: 32
              }
          },
          reference: "MYREF: 653",
          notes: "Logo Colour A26"
      },
      success : function(r) {
        console.log(r);
      }
    });
```
Response
```json
{
    "OrderId": "139424",
    "ResellerId": 9999,
    "Links": [
        {
            "Uri": "https://hublink.api.cmykhub.com/man/orders/139424",
            "Relation": "self",
            "MediaType": "application/vnd.cmykhub+json"
        },
        {
            "Uri": "https://hublink.api.cmykhub.com/accounts/payments?orderId=139424",
            "Relation": "http://schemas.cmykhub.com/api/orders/relations/payment",
            "MediaType": "text/html"
        },
        {
            "Uri": "https://hublink.api.cmykhub.com/pp/orders?orderId=139424",
            "Relation": "http://schemas.cmykhub.com/api/prepress/relations/orders/artwork",
            "MediaType": "application/vnd.cmykhub+json"
        }
    ]
}
```

## From Booklet Specification
Orders can be placed with booklet specification. Any booklet specification is valid, see [Pricing](Pricing.md) for more details on booklet specifications.

Eg
Javascript ajax request
```javascript
    $.ajax({
      url: "/man/orders",
      dataType: "json",
      type : "POST",
      data: {
          booklet: {
              quantity: 1000,
              orientation: 0,
              finishedSize: { width: 205, height: 280 },
              bindingId: "1",
              printType: 2,
              body:{
              	paperId: "215",
              	pp: 32
              },
              cover:{
              	productId: "1400"
              }
          },
          reference: "MYREF: 653",
          notes: "Logo Colour A26"
      },
      success : function(r) {
        console.log(r);
      }
    });
```
Response
```json
{
    "OrderId": "139424",
    "ResellerId": 9999,
    "Links": [
        {
            "Uri": "https://hublink.api.cmykhub.com/man/orders/139424",
            "Relation": "self",
            "MediaType": "application/vnd.cmykhub+json"
        },
        {
            "Uri": "https://hublink.api.cmykhub.com/accounts/payments?orderId=139424",
            "Relation": "http://schemas.cmykhub.com/api/orders/relations/payment",
            "MediaType": "text/html"
        },
        {
            "Uri": "https://hublink.api.cmykhub.com/pp/orders?orderId=139424",
            "Relation": "http://schemas.cmykhub.com/api/prepress/relations/orders/artwork",
            "MediaType": "application/vnd.cmykhub+json"
        }
    ]
}
```


## From Wide Format Specification
Orders can be placed with wide format product specification.

Eg
Javascript ajax request
```javascript
    $.ajax({
      url: "/man/orders",
      dataType: "json",
      type : "POST",
      data: {
          wideFormat: {
          		productId:"36db0a24-9cb7-4f54-8bee-284fcefbcd4c",
          		quantity:2,
          		kinds:1,
          		finishedSize:{ "Width":950, "Height":1400},
          		finishing:[{
          			finishingId:"b1654e5e-b5f7-4f54-9075-ed32849ff683",
          			config:{
          				spacing:"15cm"
          			}
          		}]
          	}
          },
          reference: "MYREF: 653",
          notes: "Logo Colour A26"
      },
      success : function(r) {
        console.log(r);
      }
    });
```
Response
```json
{
    "OrderId": "872492",
    "ResellerId": 9999,
    "Links": [
        {
            "Uri": "https://hublink.api.cmykhub.com/man/orders/872492",
            "Relation": "self",
            "MediaType": "application/vnd.cmykhub+json"
        },
        {
            "Uri": "https://hublink.api.cmykhub.com/accounts/payments?orderId=872492",
            "Relation": "http://schemas.cmykhub.com/api/orders/relations/payment",
            "MediaType": "text/html"
        },
        {
            "Uri": "https://hublink.api.cmykhub.com/pp/orders?orderId=872492",
            "Relation": "http://schemas.cmykhub.com/api/prepress/relations/orders/artwork",
            "MediaType": "application/vnd.cmykhub+json"
        }
    ]
}
```

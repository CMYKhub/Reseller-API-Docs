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

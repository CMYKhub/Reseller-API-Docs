# Pricing

Prices can be created for standard products as well as booklets.

Prices created through the pricing endpoints are not saved in the system, however
the prices returned will be honored for terms set out in your account with CMYKhub.
When placing an order, please include the token value returned with the price so
that the price may be honored. See the [Ordering](Orders.md) endpoint for more details.


## Standard products

<span style="color: blue">**GET**</span> /man/pricing/standard

Creates a price for the given product details.

***Product ID*** is required. This specifies the ID of the product to be priced. See [Products](Products.md) for information on how to query the products.

***Quantity*** is required. This is the number of finished items of one kind required.

***Kinds**** is required. This specifies the number of unique items of artwork to be printed.
EG, for two different names on a business card this value would be 2.

***Finished size*** is optional. This can be specified if the final size of the
product required is smaller than the standard product specified.
Units are millimetres.

***Finishing*** is optional. This can be specified for finishing required that is
additional to the finishing included with the standard product. EG bundling. See [Finishing](Finishings.md) for available finishing options.
***NoItems*** is used to indicate how many of the final product should be finished.
This must be specified, if unsure enter the same as the quantity.

Eg
Javascript ajax request
```javascript
    $.ajax({
      url: "/man/pricing/standard",
      dataType: "json",
      type : "POST",
      data: {
          productId: "12345",
          quantity: 1000,
          kinds: 2,
          finishedSize: { width: 205, height: 280 },
          finishing: [ { finishingId: "9876", noItems: 500 } ]
      },
      success : function(r) {
        console.log(r);
      }
    });
```
Response
```json
{
    "Expires": "2017-01-01T00:00:00.000Z",
    "Price": {
        "ExTax": 320,
        "Tax": 32,
        "IncTax": 352,
        "Currency": {
            "Code": "AUD"
        }
    },
    "ResellerId": "54321",
    "Token": "eyIkdHlwZSI....IXBAfqyMkvrqPe9g"
}
```





## Booklet products

<span style="color: blue">**GET**</span> /man/pricing/booklet

Creates a price for the given booklet details.

### Self cover booklets

The parameters required are the base requirements for all booklet quotes.

***Quantity*** is required. This is the number of finished items of one kind required.

***Orientation*** is required. This specifies whether the finished booklet is portrait or landscape. Portrait = 0, Landscape = 1.

***Finished size*** is optional. This specifies the final size of the
product required. Units are millimetres.

***Binding ID*** is required. This is the binding finishing. See [Finishing](Finishings.md) for available binding options.

***Print Type*** is required. This specifies whether the product should be printed offset or digital. Offset = 1, Digital = 2.

***Body*** is required. This specifies the body section details.
***Body.PaperID*** is required. This specifies the paper to be used for the body section. See [Paper](Papers.md) for available paper options.
***Body.PP*** is required. This specifies the number of printed pages for the body section. This must be a multiple of 4.

Eg
Javascript ajax request
```javascript
    $.ajax({
      url: "/man/pricing/booklet",
      dataType: "json",
      type : "POST",
      data: {
          quantity: 1000,
          orientation: 0,
          finishedSize: { width: 205, height: 280 },
          bindingId: "1",
          printType: 2,
          body:{
          	paperId: "215",
          	pp: 32
          },
      },
      success : function(r) {
        console.log(r);
      }
    });
```
Response
```json
{
    "Expires": "2017-01-01T00:00:00.000Z",
    "Price": {
        "ExTax": 1598.39,
        "Tax": 159.84,
        "IncTax": 1758.23,
        "Currency": {
            "Code": "AUD"
        }
    },
    "ResellerId": "54321",
    "Token": "eyIkdHlwZSI....IXBAfqyMkvrqPe9g"
}
```



### Product cover booklets

The parameters required are in addition to the self cover parameters.

***Cover*** is optional. This specifies the cover section details.
***Cover.ProductId*** is required for product covers. If specified then pp and paperId should be left empty. This specifies the product to be used for the cover section. See [Products](Products.md) for available products. Note: the product size must match the size of the leaf in the booklet. EG for a portrait A4 finished size book, the leaf size must be A3.

***Cover.Finishing*** is optional. This can be specified for finishing required that is
additional to the finishing included with the standard product. EG bundling. See [Finishing](Finishings.md) for available finishing options.
***NoItems*** is used to indicate how many of the final product should be finished.
This must be specified, if unsure enter the same as the quantity.

Eg
Javascript ajax request
```javascript
    $.ajax({
      url: "/man/pricing/booklet",
      dataType: "json",
      type : "POST",
      data: {
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
      success : function(r) {
        console.log(r);
      }
    });
```
Response
```json
{
    "Expires": "2017-01-01T00:00:00.000Z",
    "Price": {
        "ExTax": 1598.39,
        "Tax": 159.84,
        "IncTax": 1758.23,
        "Currency": {
            "Code": "AUD"
        }
    },
    "ResellerId": "54321",
    "Token": "eyIkdHlwZSI....IXBAfqyMkvrqPe9g"
}
```


### Custom cover booklets

The parameters required are in addition to the self cover parameters.

***Cover*** is optional. This specifies the cover section details.
***Cover.PaperId*** is required for custom covers. If specified then productId should be left empty and pp should be specified. This specifies the id of the paper to be used for the cover section. See [Papers](Papers.md) for available papers.
***Cover.PP*** is required for custom covers. This specifies whether the cover is 2pp (single sided) or 4pp (double sided).

***Cover.Finishing*** is optional. This can be specified for finishing required that is
additional to the finishing included with the standard product. EG bundling. See [Finishing](Finishings.md) for available finishing options.
***NoItems*** is used to indicate how many of the final product should be finished.
This must be specified, if unsure enter the same as the quantity.

Eg
Javascript ajax request
```javascript
    $.ajax({
      url: "/man/pricing/booklet",
      dataType: "json",
      type : "POST",
      data: {
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
          	paperId:"163",
          	pp:2,
          	finishing:[
          		{ finishingId:"142", noItems:250}
          		]
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
    "Expires": "2017-01-01T00:00:00.000Z",
    "Price": {
        "ExTax": 1785.46,
        "Tax": 178.55,
        "IncTax": 1964.01,
        "Currency": {
            "Code": "AUD"
        }
    },
    "ResellerId": "54321",
    "Token": "eyIkdHlwZSI....IXBAfqyMkvrqPe9g"
}
```

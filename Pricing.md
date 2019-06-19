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
            "Code": "AUD",
			"Symbol": "$"
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
          finishedSize: { width: 210, height: 297 },
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
            "Code": "AUD",
			"Symbol": "$"
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
          finishedSize: { width: 210, height: 297 },
          bindingId: "1",
          printType: 2,
          body:{
          	paperId: "215",
          	pp: 32
          },
          cover:{
          	productId: "1400",
			pp: 2
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
            "Code": "AUD",
			"Symbol": "$"
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
          finishedSize: { width: 210, height: 297 },
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
          		{ finishingId:"1", noItems:250}
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
            "Code": "AUD",
			"Symbol": "$"
        }
    },
    "ResellerId": "54321",
    "Token": "eyIkdHlwZSI....IXBAfqyMkvrqPe9g"
}
```


## Wide Format products

<span style="color: blue">**GET**</span> /man/pricing/wideFormat

Creates a price for the given wide format product details.

***Product ID*** is required. This specifies the ID of the product to be priced. See [Products](Products.md) for information on how to query the products.

***Quantity*** is required. This is the number of finished items of one kind required.

***Kinds**** is required. This specifies the number of unique items of artwork to be printed.
EG, for two different images on a poster this value would be 2.

***Finished size*** is optional depending on the product. If the product has a fixed size then this must not be specified.
 If the product has a variable size this must be specified
Units are millimetres.

***Finishing*** is optional depending on the product. This must be specified for finishing that is
part of the product and required configuration. EG for a product with eyelets, this must be specified. 
Config is used to configure the values for the fields


Eg
Javascript ajax request (product with no finishing config required)
```javascript
    $.ajax({
      url: "/man/pricing/wideFormat",
      dataType: "json",
      type : "POST",
      data: {
          productId: "01483075-4937-4f74-8de9-9b8d67aa647d",
          quantity: 3,
          kinds: 2,
          finishedSize: { width: 950, height: 1200 }
      },
      success : function(r) {
        console.log(r);
      }
    });
```
Response
```json
{
    "Expires": "2018-08-27T00:00:00+08:00",
    "Price": {
        "ExTax": 105.61,
        "Tax": 10.56,
        "IncTax": 116.17,
        "Currency": {
            "Code": "AUD",
            "Symbol": "$"
        }
    },
    "ResellerId": "54321",
    "Token": "eyIkdHlwZSI....IXBAfqyMkvrqPe9g"
}
```



Eg
Javascript ajax request (product with finishing config required, eg eyelets)
```javascript
    $.ajax({
      url: "/man/pricing/wideFormat",
      dataType: "json",
      type : "POST",
      data: {
          productId: "21eb8be8-fbf0-4c0d-806e-24cebbb9de5b",
          quantity: 3,
          kinds: 2,
          finishedSize: { width: 950, height: 1200 },
	      finishing:[{
		        finishingId: "b1f1710c-deb6-4a6a-aaa7-98c5b72d3246",
		        config:{
			        "Spacing": "15cm"
		        }
	        }]
      },
      success : function(r) {
        console.log(r);
      }
    });
```
Response
```json
{
    "Expires": "2018-08-27T00:00:00+08:00",
    "Price": {
        "ExTax": 77.22,
        "Tax": 7.72,
        "IncTax": 84.94,
        "Currency": {
            "Code": "AUD",
            "Symbol": "$"
        }
    },
    "ResellerId": "54321",
    "Token": "eyIkdHlwZSI....IXBAfqyMkvrqPe9g"
}
```




# Orders


<span style="color: blue">**GetOrdersAsync**</span>

Returns orders for the reseller specified by the ResellerID header.

Orders can be filtered by orderId to return a single order.

Eg .Net C# request to get all orders
```csharp
	public async Task<IEnumerable<Order>> GetOrders()
	{
		return await ManufacturingClient.GetOrdersAsync();
	}
```
Eg .Net C# request to get order from order id
```csharp
	public async Task<Order> GetOrder(string id)
	{
		return await ManufacturingClient.GetOrderAsync(id);
	}
```

Json Response
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





<span style="color: blue">**CreateOrderAsync**</span>

Creates an order for print.

## Existing Quote
Orders can be placed with reference to an existing quote.

Eg .Net C# request to create order from a request containing a quote id
```csharp
#region Assembly CMYKhub.ResellerApi.Client, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
#endregion

namespace CMYKhub.ResellerApi.Client.Manufacturing
{
    public class CreateOrderFromQuoteRequest : CreateOrderRequest
    {
        public CreateOrderFromQuoteRequest();

        public string QuoteId { get; set; }
    }
}

_____

	var request = new CreateOrderFromQuoteRequest { QuoteId = "98765" };
	
	public async Task<CreatedOrderResource> CreateOrder(CreateOrderFromQuoteRequest request)
	{
		return await ManufacturingClient.CreateOrderAsync(request);
	}
```

Json Response
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

Eg .Net C# request to create an order from a token
```csharp
#region Assembly CMYKhub.ResellerApi.Client, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
#endregion

namespace CMYKhub.ResellerApi.Client.Manufacturing
{
    public abstract class CreateOrderFromWizardRequest : CreateOrderRequest
    {
        protected CreateOrderFromWizardRequest();

        public string Notes { get; set; }
        public string Reference { get; set; }
    }

    public class CreateOrderFromTokenRequest : CreateOrderFromWizardRequest
    {
        public CreateOrderFromTokenRequest();

        public string Token { get; set; }
    }
}

_____

	request = new CreateOrderFromTokenRequest
	{
		Token = "BEDD7831-75C5-48DD-861C-E8181EE66FCE",
		Reference = "MYREF: 653",
		Notes = "Logo Colour A26"
	};

	public async Task<CreatedOrderResource> CreateOrder(CreateOrderFromTokenRequest request)
	{
		return await ManufacturingClient.CreateOrderAsync(request);
	}
```
Json Response
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
.Net C# request to create an order from a product
```csharp
#region Assembly CMYKhub.ResellerApi.Client, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
#endregion

namespace CMYKhub.ResellerApi.Client.Manufacturing
{
    public abstract class CreateOrderFromWizardRequest : CreateOrderRequest
    {
        protected CreateOrderFromWizardRequest();

        public string Notes { get; set; }
        public string Reference { get; set; }
    }

    public class CreateOrderFromProductRequest : CreateOrderFromWizardRequest
    {
        public CreateOrderFromProductRequest();

        public StandardPriceRequest Product { get; set; }
    }
}

_____

	request = new CreateOrderFromProductRequest
	{
		Product = new StandardPriceRequest
		{
			ProductId = "01B80D34-4B6C-4D80-9C02-501762670EEE",
			Quantity = 1000,
			Kinds = 2,
			FinishedSize = new Size { Width = 205, Height = 280 },
			Finishing = new[]
			{
				new PrintWizardFinishing {FinishingId = "14", NoItems = 500}
			}
		},
		Reference = "MYREF: 653",
		Notes = "Logo Colour A26"
	};

	public async Task<CreatedOrderResource> CreateOrder(CreateOrderFromProductRequest request)
	{
		return await ManufacturingClient.CreateOrderAsync(request);
	}
```
Json Response
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
.Net C# request to create an order from a booklet
```csharp
#region Assembly CMYKhub.ResellerApi.Client, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
#endregion

namespace CMYKhub.ResellerApi.Client.Manufacturing
{
    public abstract class CreateOrderFromWizardRequest : CreateOrderRequest
    {
        protected CreateOrderFromWizardRequest();

        public string Notes { get; set; }
        public string Reference { get; set; }
    }

    public class CreateOrderFromBookletRequest : CreateOrderFromWizardRequest
    {
        public CreateOrderFromBookletRequest();

        public BookletProductRequest Booklet { get; set; }
    }
}

_____

	request = new CreateOrderFromBookletRequest
	{
		Booklet = new BookletProductRequest
		{
			Quantity = 1000,
			Orientation = 0,
			FinishedSize = new Size { Width = 210, Height = 297 },
			BindingId = "1",
			PrintType = 2,
			Body = new BookletBodySection
			{
				PaperId = "215",
				Pp = 32
			},
			Cover = new BookletCoverSection
			{
				ProductId = "1400",
				Pp = 2
			}
		},
		Reference = "MYREF: 653",
		Notes = "Logo Colour A26"
	};

	public async Task<CreatedOrderResource> CreateOrder(CreateOrderFromBookletRequest request)
	{
		return await ManufacturingClient.CreateOrderAsync(request);
	}
```
Json Response
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
.Net C# request to create an order from a wide format product
```csharp
#region Assembly CMYKhub.ResellerApi.Client, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
#endregion

namespace CMYKhub.ResellerApi.Client.Manufacturing
{
    public abstract class CreateOrderFromWizardRequest : CreateOrderRequest
    {
        protected CreateOrderFromWizardRequest();

        public string Notes { get; set; }
        public string Reference { get; set; }
    }

    public class CreateOrderFromWideFormatRequest : CreateOrderFromWizardRequest
    {
        public CreateOrderFromWideFormatRequest();

        public WideFormatPriceRequest WideFormat { get; set; }
    }
}

_____

	request = new CreateOrderFromWideFormatRequest
	{
		WideFormat = new WideFormatPriceRequest
		{
			ProductId = "F74ADCFE-AAD5-43EB-A9E5-66144B8A762F",
			Quantity = 2,
			Kinds = 1,
			FinishedSize = new Size { Width = 950, Height = 1500 },
			Finishing = new[]
			{
				new WideFormatWizardFinishing
				{
					FinishingId = "BDAF621E-18C4-4CF0-AF3D-541EC894F67A",
					Config = new Dictionary<string, string> {{"Spacing", "15cm"}}
				}
			}
		},
		Reference = "MYREF: 653",
		Notes = "Logo Colour A26"
	};
			
    public async Task<CreatedOrderResource> CreateOrder(CreateOrderFromWideFormatRequest request)
    {
    	return await ManufacturingClient.CreateOrderAsync(request);
    }
```
Json Response
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

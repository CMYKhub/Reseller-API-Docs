# REST API Reference

Getting started with the API client.

There are two clients which need to be accessed to call the methods below:
1. Hublink Manufacturing Client
2. Hublink Prepress Client

<span style="color: blue">**HublinkManufacturingClient**</span>

```csharp
	private string _apiUrl = "https://api.cmykhub.com";
	private string _resellerId = "9876";
	private string _apiKey = "aBcDeFg1234";

	private ClientSettings ClientSettings => new ClientSettings(_apiUrl, _resellerId, _apiKey);
	
	private HublinkManufacturingClient ManufacturingClient => new HublinkManufacturingClient(new HttpClientFactory(), ClientSettings)
```

<span style="color: blue">**HublinkPrepressClient**</span>

```csharp
	private string _apiUrl = "https://api.cmykhub.com";
	private string _resellerId = "9876";
	private string _apiKey = "aBcDeFg1234";

	private ClientSettings ClientSettings => new ClientSettings(_apiUrl, _resellerId, _apiKey);
	
	private HublinkPrepressClient PrepressClient => new HublinkPrepressClient(new HttpClientFactory(), ClientSettings)
```

* [Uploads](Uploads.md)
* [Customers](Customers.md)
* [Orders](Orders.md)
* [Papers](Papers.md)
* [Finishing's](Finishings.md)
* [Products](Products.md)
* [Pricing](Pricing.md)

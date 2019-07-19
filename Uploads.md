
## Uploads

Create artwork package for an order

<span style="color: blue">**UploadArtworkAsync**</span>

Create a new artwork file resource.

Eg .Net C# Upload
```csharp
	var orderId = "123456";
	var filename = "MyArtwork.pdf";

	public async Task<Order> GetOrder(string id)
	{
		return await ManufacturingClient.GetOrderAsync(id);
	}

	public async Task Upload(string orderId, string filename)
	{
		var order = await GetOrder(orderId);
		await PrepressClient.UploadArtworkAsync(orderId, order.HubId, new[] { filename });
	}
```

There is no response for this method

Json Response
```json
{}
```

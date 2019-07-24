# Products


<span style="color: blue">**GetProductsAsync**</span>
<br/>
<span style="color: blue">**GetProductsByNameAsync**</span>

Returns standard products optionally filtered by name.

Eg .Net C# request to get Products
```csharp
	var name = "gloss";
	
	public async Task<IEnumerable<Product>> GetProducts(string name = null)
	{
		var asyncProducts = string.IsNullOrEmpty(name)
			? ManufacturingClient.GetProductsAsync()
			: ManufacturingClient.GetProductsByNameAsync(name);
		return await asyncProducts;
	}
```
Json Response
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
<span style="color: blue">**GetProductAsync**</span>

Eg .Net C# request to get Product by Id
```csharp
	public async Task<Product> GetProduct(string id)
	{
		return await ManufacturingClient.GetProductAsync(id);
	}
```
Json Response
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




<span style="color: blue">**GetWideFormatProductsAsync**</span>
<br/>
<span style="color: blue">**GetWideFormatProductsByNameAsync**</span>

Returns wide format products optionally filtered by name.

Eg .Net C# request to get Wide format Products
```csharp
	var name = "canvas"
	public async Task<IEnumerable<Product>> GetProductsWideFormat(string name = null)
	{
		var asyncProducts = string.IsNullOrEmpty(name)
			? ManufacturingClient.GetWideFormatProductsAsync()
			: ManufacturingClient.GetWideFormatProductsByNameAsync(name);
		return await asyncProducts;
	}
```
Json Response
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

<span style="color: blue">**GetWideFormatProductAsync**</span>


Eg .Net C# request to get Wide format Product by Id
```csharp
	public async Task<Product> GetProductWideFormat(string id)
	{
		return await ManufacturingClient.GetWideFormatProductAsync(id);
	}
```
Json Response
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

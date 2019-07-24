# Paper Sizes

<span style="color: blue">**GetFixedSizesAsync**</span>
<br/>
<span style="color: blue">**GetFixedSizeAsync**</span>

Returns Fixed Paper sizes.

Fixed Paper sizes can be filtered by sizeId to return a single size, or by quote type to return sizes which are relevant to the type of quote.

Eg .Net C# request to get all sizes
```csharp
	public async Task<IEnumerable<Size>> GetFixedSizes()
	{
		return await ManufacturingClient.GetFixedSizesAsync();
	}
```
Eg .Net C# request to get all sizes
```csharp
	public async Task<IEnumerable<Size>> GetFixedSizes(string quoteType)
	{
		return await ManufacturingClient.GetFixedSizesAsync(quoteType);
	}
```

Json Response
```json
{
    "Items": [
        {
            "Id": "10",
            "Name": "DL",
            "Width": 210,
            "Height": 99
        },
        {
            "Id": "7",
            "Name": "A5",
            "Width": 210,
            "Height": 148
        },
        {
            "Id": "6",
            "Name": "A4",
            "Width": 297,
            "Height": 210
        }
    ]
}
```
Eg .Net C# request to get paper size from size id
```csharp
	public async Task<FixedSize> GetFixedSize(string id)
	{
		return await ManufacturingClient.GetFixedSizeAsync(id);
	}
```

Json Response
```json
{
	"Id": "6",
	"Name": "A4",
	"Width": 297,
	"Height": 210,
    "Links": [
        {
            "Uri": "http://localhost:50595/man/fixedsize/6",
            "Relation": "self",
            "MediaType": "application/vnd.cmykhub+json"
        }
    ]
}
```

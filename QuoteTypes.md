# Quote Types

<span style="color: blue">**GetQuoteTypesAsync**</span>

Returns Quote types.

Eg .Net C# request to get quote types
```csharp
	public async Task<IEnumerable<string>> GetQuoteTypes()
	{
		return await ManufacturingClient.GetQuoteTypesAsync();
	}
```

Json Response
```json
{
    [
		"Invalid",
		"FlatSheet",
		"BasicBooklet",
		"Product",
		"Custom",
		"CentreGroup",
		"NotAvailable",
		"WideFormat"
    ]
}
```

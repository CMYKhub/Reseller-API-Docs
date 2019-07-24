# Papers


<span style="color: blue">**GetPapersAsync**</span>
<br/>
<span style="color: blue">**GetPapersByNameAsync**</span>

Returns papers optionally filtered by name.

Eg .Net C# request to get all papers, or papers which match the name
```csharp
	public async Task<IEnumerable<Paper>> GetPapers(string name = null)
	{
		var papersAsync = string.IsNullOrEmpty(name)
			? ManufacturingClient.GetPapersAsync()
			: ManufacturingClient.GetPapersByNameAsync(name);
		return await papersAsync;
	}
```
Json Response
```json
{
    "Items": [
        {
            "Id": "356",
            "Description": "EcoStar Uncoated 100% Recycled  ",
            "Links": [
                {
                    "Uri": "https://hublink.api.cmykhub.com/man/Papers/356",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        },
        {
            "Id": "357",
            "Description": "EcoStar Uncoated 100% Recycled  ",
            "Links": [
                {
                    "Uri": "https://hublink.api.cmykhub.com/man/Papers/357",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        }
    ]
}
```

<span style="color: blue">**GetPaperAsync**</span>

Eg .Net C# request to get all papers, or papers which match the name
```csharp
	public async Task<Paper> GetPaper(string id)
	{
		return await ManufacturingClient.GetPaperAsync(id);
	}
```
Json Response
```json
{
    "Id": "356",
    "Description": "EcoStar Uncoated 100% Recycled  ",
    "Family": "EcoStar Uncoated 100% Recycled",
    "Colour": "",
    "Texture": "",
    "Weight": 100,
    "Links": [
        {
            "Uri": "https://hublink.api.cmykhub.com/man/Papers/356",
            "Relation": "self",
            "MediaType": "application/vnd.cmykhub+json"
        }
    ]
}
```

# Finishings


<span style="color:blue">**GetFinishingsAsync**</span>
<br/>
<span style="color:blue">**GetFinishingsByNameAsync**</span>

Returns finishings optionally filtered by name.

Eg .Net C# request to get all finishings, or finishings which match the name
```csharp
	public async Task<IEnumerable<Finishing>> GetFinishings(string name = null)
	{
		var asyncFinishings = string.IsNullOrEmpty(name)
			? ManufacturingClient.GetFinishingsAsync()
			: ManufacturingClient.GetFinishingsByNameAsync(name);
		return await asyncFinishings;
	}
```
Json Response
```json
{
    "Items": [
        {
            "Id": "85",
            "Name": "Double gate fold 8pp A4",
            "Links": [
                {
                    "Uri": "https://hublink.api.cmykhub.com/man/Finishings/85",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        },
        {
            "Id": "45",
            "Name": "Fold - 10pp DL Concertina (no scoring)",
            "Links": [
                {
                    "Uri": "https://hublink.api.cmykhub.com/man/Finishings/45",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        }
    ]
}
```
<span style="color:blue">**GetFinishingAsync**</span>

Eg .Net C# request to get finishing by id
```csharp
	public async Task<Finishing> GetFinishing(string id)
	{
		return await ManufacturingClient.GetFinishingAsync(id);
	}
```
Json Response
```json
{
    "Id": "85",
    "Name": "Double gate fold 8pp A4",
    "Description": "",
    "Type": {
        "Id": "0",
        "Name": "SingleItemSheet"
    },
    "Links": [
        {
            "Uri": "https://hublink.api.cmykhub.com/man/Finishings/85",
            "Relation": "self",
            "MediaType": "application/vnd.cmykhub+json"
        }
    ]
}
```

## Finishing/Available

<span style="color:blue">**GetFinishingsByAvailableAsync**</span>

Returns finishings available for a given specification.

*width:* The width of the trimmed product in millimetres.

*height:* The height of the trimmed product in millimetres.

*paperWeight:* The weight of the paper in gsm.

*printType:* The type of printing (1=Offset, 2=Digital,
3=Offset OR Digital).

*book.pp:* The number of printed pages in the book.
NB if any book parameters are specified then all
book parameters must be specified.

*book.orientation:* The orientation of the book
(0=Portrait, 1=Landscape).
NB if any book parameters are specified then all
book parameters must be specified.


Eg .Net C# request to get finishings
```csharp
	private PrintTypes[] GetPrintType = { PrintTypes.Offset, PrintTypes.Digital };

	public async Task<IEnumerable<Finishing>> GetFinishings(int width, int height, int paperWeight, int printType)
	{
		return await ManufacturingClient.GetFinishingsByAvailableAsync(new FinishingAvailableSpec
		{
			Width = width,
			Height = height,
			PaperWeight = paperWeight,
			PrintType = GetPrintType[printType]
		});
	}
```
Json Response
```json
{
    "Items": [
        {
            "Id": "2",
            "Name": "Fold - Roll fold A4 to DL",
            "Links": [
                {
                    "Uri": "https://hublink.api.cmykhub.com/man/Finishings/2",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        },
        {
            "Id": "4",
            "Name": "Fold - Single fold in half",
            "Links": [
                {
                    "Uri": "https://hublink.api.cmykhub.com/man/Finishings/4",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        },
        {
            "Id": "6",
            "Name": "Fold - 6pp DL Roll Fold (Outer-98/99/100mm, Inner-100/99/98mm)",
            "Links": [
                {
                    "Uri": "https://hublink.api.cmykhub.com/man/Finishings/6",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        }
    ]
}
```

**For booklet finishing:**

Eg .Net C# request to get finishings
```csharp
	private PrintTypes[] GetPrintType = { PrintTypes.Offset, PrintTypes.Digital };
	private Orientations[] GetOrientations = { Orientations.Landscape, Orientations.Portrait };
	
	public async Task<IEnumerable<Finishing>> GetFinishings(int width, int height, int paperWeight, int printType, int pp, int orientation)
	{
		return await ManufacturingClient.GetFinishingsByAvailableAsync(new FinishingAvailableSpec
		{
			Width = width,
			Height = height,
			PaperWeight = paperWeight,
			PrintType = GetPrintType[printType],
			Book = new FinishingAvailableBookletSpec { Orientation = GetOrientations[orientation], Pp = pp }
		});
	}
```
Json Response
```json
{
    "Items": [
        {
            "Id": "1",
            "Name": "Saddle Staple",
            "Links": [
                {
                    "Uri": "https://hublink.api.cmykhub.com/man/Finishings/1",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        },
        {
            "Id": "86",
            "Name": "Perfect Bind",
            "Links": [
                {
                    "Uri": "https://hublink.api.cmykhub.com/man/Finishings/86",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        },
        {
            "Id": "129",
            "Name": "Wire Bind",
            "Links": [
                {
                    "Uri": "https://hublink.api.cmykhub.com/man/Finishings/129",
                    "Relation": "self",
                    "MediaType": "application/vnd.cmykhub+json"
                }
            ]
        }
    ]
}
```

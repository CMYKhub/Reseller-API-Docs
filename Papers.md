# Papers


<span style="color: blue">**GET**</span> /man/papers

Returns papers optionally filtered by name.

Eg
Javascript ajax request
```javascript
    $.ajax({
      url: "/man/papers?name=uncoated",
      dataType: "json",
      type : "GET",
      success : function(r) {
        console.log(r);
      }
    });
```
Response
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

Javascript ajax request
```javascript
    $.ajax({
      url: "/man/papers/356",
      dataType: "json",
      type : "GET",
      success : function(r) {
        console.log(r);
      }
    });
```
Response
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

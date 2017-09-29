
## Uploads

The basic sequence to upload a file is as follows:
1. Create a new resource for the artwork file
2. Upload file content (in chunks)
3. Patch MD5 \**Optional: See Note Below*
4. Repeat steps 1-3 for each file to upload
5. Create artwork package for an order

\* MD5 checksum is used for the server to verify the integrity of the received bytes. The file will remain in an unverified state until the calculated MD5 matches the supplied MD5. If the MD5 checksum is known before uploading the file then this can be supplied when creating the new file resource (step 1 above). If the MD5 is calculated as part of the upload process then it can be patched at the end of uploading the chunks. The server will consider the file uploaded successfully once the MD5 checksum matches, no matter if it is supplied before or after.


<span style="color: blue">**POST**</span> /pp/artwork

Create a new artwork file resource.

Eg
Javascript ajax request
```javascript
    $.ajax({
      url: "/pp/uploads",
      dataType: "json",
      type: "POST",
      data: {
          orderId: "123456",
          filename: "MyArtwork.pdf",
          fileLength: 54278,
          contentType: "application/pdf"
      },
      success: function(r) {
        console.log(r);
      }
    });
```
Response
```json
{
    "Id": "117e5c28-0b35-4466-9842-2605036a92b6",
    "PackageId": null,
    "Filename": "MyArtwork.pdf",
    "MD5Hash": "",
    "ContentType": "application/pdf",
    "UploadedBy": "Your Name",
    "UploadedById": "6543",
    "Status": { "Id": 0, "Name": "Incomplete" },
    "UploadDate": "2017-09-29T08:00:00.0000000Z",
    "Links": [
        {
            "Uri": "http://tempuri.org/pp/Uploads/123456/Artwork/117e5c28-0b35-4466-9842-2605036a92b6",
            "Relation": "self",
            "MediaType": "application/json"
        },
        {
            "Uri": "http://tempuri.org/pp/Uploads/123456/Artwork/117e5c28-0b35-4466-9842-2605036a92b6/Chunks",
            "Relation": "http://schemas.cmykhub.com/api/Relations/Files/Chunks",
            "MediaType": "application/octet-stream"
        },
        {
            "Uri": "http://tempuri.org/pp/Uploads/123456/Artwork/117e5c28-0b35-4466-9842-2605036a92b6/Content",
            "Relation": "http://schemas.cmykhub.com/api/Relations/Files",
            "MediaType": "application/octet-stream"
        }
    ]
}
```




Upload binary file content

Eg Javascript ajax request
```javascript
    var file = document.getElementById('ArtworkFile').files[0];

    var file_size = file.size;
    var chunk_size = (1024 * 100); // 100KB
    var range_start = 0;
    var range_end = chunk_size;        
    var chunk;    
    var chunks_sent=0;
    var spark;
    var _errorCount = 0;
    var _md5ChecksumStartPos = [];

    // Prevent range overflow
    if (range_end > file_size) {
        range_end = file_size;
    }

    chunk = file.slice(range_start, range_end);

    var arrayBuffer;
    var fileReader = new FileReader();
    fileReader.onload = (ev) => {
        var contents = ev.target;
        arrayBuffer = contents.result;
    };
    fileReader.readAsArrayBuffer(chunk);
    fileReader.onloadend = function(ect){

        //this code prevents the MD5 appending more than once in the event we are retrying a chunk
        if (_md5ChecksumStartPos.indexOf(range_start) < 0) {
            _md5ChecksumStartPos.push(range_start);
            spark.append(arrayBuffer);
        }

        upload_request.open('POST', chunk_url, true);
        if (upload_request.overrideMimeType)
            upload_request.overrideMimeType('application/octet-stream');

        //help the api determine what chunk is being sent
        upload_request.setRequestHeader('Content-Range', 'bytes ' + range_start + '-' + range_end + '/' + file_size);

        //chunk md5 calculation
        var chunkMd5Spark = new SparkMD5.ArrayBuffer();
        chunkMd5Spark.append(arrayBuffer);
        var chunkmd5Hash = chunkMd5Spark.end();
        upload_request.setRequestHeader('Content-MD5', chunkmd5Hash);

        upload_request.send(chunk);
    };

```




Patch artwork file resource MD5 checksum.

Eg
Javascript ajax request
```javascript
    $.ajax({
      url: "/pp/Uploads/123456/Artwork/117e5c28-0b35-4466-9842-2605036a92b6",
      dataType: "json",
      type: "PATCH",
      data: {
           MD5Hash: md5
      },
      success: function(r) {
        console.log(r);
      }
    });
```
Response
```json
{
    "Id": "117e5c28-0b35-4466-9842-2605036a92b6",
    "PackageId": null,
    "Filename": "MyArtwork.pdf",
    "MD5Hash": "",
    "ContentType": "application/pdf",
    "UploadedBy": "Your Name",
    "UploadedById": "6543",
    "Status": { "Id": 1, "Name": "Uploaded" },
    "UploadDate": "2017-09-29T08:00:00.0000000Z",
    "Links": [
        {
            "Uri": "http://tempuri.org/pp/Uploads/123456/Artwork/117e5c28-0b35-4466-9842-2605036a92b6",
            "Relation": "self",
            "MediaType": "application/json"
        },
        {
            "Uri": "http://tempuri.org/pp/Uploads/123456/Artwork/117e5c28-0b35-4466-9842-2605036a92b6/Chunks",
            "Relation": "http://schemas.cmykhub.com/api/Relations/Files/Chunks",
            "MediaType": "application/octet-stream"
        },
        {
            "Uri": "http://tempuri.org/pp/Uploads/123456/Artwork/117e5c28-0b35-4466-9842-2605036a92b6/Content",
            "Relation": "http://schemas.cmykhub.com/api/Relations/Files",
            "MediaType": "application/octet-stream"
        }
    ]
}
```





Create order artwork package resource.

Eg
Javascript ajax request
```javascript
    $.ajax({
      url: "/pp/Orders/Artwork",
      dataType: "json",
      type: "POST",
      data: {
          orderId: "123456",
          hubId: "5",
          files: [{
            contentType: "application/pdf",
            name: "MyArtwork.pdf",
            url: "http://tempuri.org/pp/Uploads/123456/Artwork/117e5c28-0b35-4466-9842-2605036a92b6/Content",
          }]
      },
      success: function(r) {
        console.log(r);
      }
    });
```
Response
```json
{}
```

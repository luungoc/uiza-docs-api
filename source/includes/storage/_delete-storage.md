## Remove storage


> Example Request

```shell
curl -X DELETE \
  https://#{workspace_api_domain}/api/public/v3/media/storage \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json'
  -d '{
       "id":"cd003123-7ec9-4f3a-9d7c-f2de93e83e49"
  }'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

begin
  storage = Uiza::Storage.remove "your-storage-id"
  puts storage.id
rescue Uiza::Error::UizaError => e
  puts "description_link: #{e.description_link}"
  puts "code: #{e.code}"
  puts "message: #{e.message}"
rescue StandardError => e
  puts "message: #{e.message}"
end
```

```python
import uiza

from uiza.api_resources.storage import Storage
from uiza.exceptions import ServerException

uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
uiza.authorization = "your-authorization"

try:
  res, status_code = Storage().remove("your-storage-id")

  print("res ", res)
except ServerException as e:
  raise e
except Exception as e:
  raise e
```

```php
<?php
require __DIR__."/../vendor/autoload.php";

Uiza\Base::setWorkspaceApiDomain("your-workspace-api-domain.uiza.co");
Uiza\Base::setAuthorization("your-authorization");

try {
  Uiza\Storage::remove("your-storage-id");
} catch(\Uiza\Exception\ErrorResponse $e) {
  print($e);
}
?>
```

```java
import java.util.*;
import com.google.gson.*;

import io.uiza.Uiza;
import io.uiza.exception.*;
import io.uiza.model.Storage;
import io.uiza.model.Storage.*;

public class Main {

  public static void main(String[] args) {
    Uiza.workspaceApiDomain = "your-workspace-api-domain.uiza.co";
    Uiza.authorization = "your-authorization";

    try {
      JsonObject response = Storage.remove("<storage-id>");
      System.out.println(response);
    } catch (UizaException e) {
      System.out.println("Status is: " + e.getStatusCode());
      System.out.println("Message is: " + e.getMessage());
      System.out.println("Description link is: " + e.getDescriptionLink());
    } catch (Exception e) {
      System.out.println(e);
    }
  }
}
```

```javascript
const uiza = require('uiza');
uiza.workspace_api_domain('your-workspace-api-domain.uiza.co');
uiza.authorization('your-authorization-key');

uiza.storage.remove('your-storage-id')
  .then((res) => {
    //Identifier of storage has been removed
  }).catch((err) => {
    //Error
  });
```

```go
import (
  uiza "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/storage"
)

func init() {
  Uiza.WorkspaceAPIDomain = "your-workspace-api-domain.uiza.co"
  Uiza.Authorization = "your-authorization"
}

params := &uiza.StorageRemoveParams{ID: uiza.String("your-storage-id")}
response, err := storage.Remove(params)
if err != nil {
  log.Printf("%v\n", err)
} else {
  log.Printf("%v\n", response)
}
```

```csharp
using System;
using Uiza.Net.Configuration;
using Uiza.Net.Enums;
using Uiza.Net.Parameters;
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  WorkspaceApiDomain = "your-workspace-api-domain.uiza.co",
  Authorization = "your-authorization"
});

try
{
  var result = UizaServices.Storage.Remove("your-storage-id");

  Console.WriteLine(string.Format("Remove Storage Id = {0} Success", result.Data.id));
  Console.ReadLine();
}
catch (UizaException ex)
{
  Console.WriteLine(ex.Message);
  Console.ReadLine();
}
```

Remove storage that added to Uiza

> Example Response

```json
{
    "data": {
        "id": "cd003123-7ec9-4f3a-9d7c-f2de93e83e49",
       },
    "version": 3,
    "datetime": "2018-06-19T03:18:14.862Z",
    "policy": "public",
    "requestId": "f5ebaa82-95de-4ce7-8089-21a919ba88cb",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="delete-button"> DELETE </span>
```https://#{workspace_api_domain}/api/public/v3/media/storage```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| **Authorization** | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **id** | *string* | Identifier of storage | **Yes** |



**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of storage has been removed |

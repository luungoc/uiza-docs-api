## Type

> Example Request

```shell
curl -X GET \
  'https://#{workspace_api_domain}/api/public/v3/analytic/entity/video-quality/type?start_date=2018-09-01&end_date=2018-11-25&type_filter=country' \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

params = {
  start_date: "YYYY-MM-DD hh:mm",
  end_date: "YYYY-MM-DD hh:mm",
  type_filter: "country"
}

begin
  response = Uiza::Analytic.get_type params
  puts response.first.name
  puts response.first.total_view
  puts response.first.percentage_of_view
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

from uiza.api_resources.analytic import Analytic
from uiza.exceptions import ServerException

uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
uiza.authorization = "your-authorization"

try:
  res, status_code = Analytic().get_type(
    start_date="2018-11-01 20:00",
    end_date="2019-11-02 20:00",
    type_filter="country"
  )

  print("res ", res)
except ServerException as e:
  raise e
except Exception as e:
  raise e
```

```php
<?
require __DIR__."/../vendor/autoload.php";

Uiza\Base::setWorkspaceApiDomain("your-workspace-api-domain.uiza.co");
Uiza\Base::setAuthorization("your-authorization");

$params = [
  "start_date" => "YYYY-MM-DD",
  "end_date" => "YYYY-MM-DD",
  "type_filter" => "country"
];

try {
  Uiza\Analytic::getType($params);
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
import io.uiza.model.Analytic;
import io.uiza.model.Analytic.*;

public class Main {

  public static void main(String[] args) {
    Uiza.workspaceApiDomain = "your-workspace-api-domain.uiza.co";
    Uiza.authorization = "your-authorization";

    Map<String, Object> params = new HashMap<>();
    params.put("start_date", "2019-01-01");
    params.put("end_date", "2019-03-01");
    params.put("type_filter", TypeFilter.COUNTRY.toString());

    try {
      JsonArray response = Analytic.getType(params);
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

const params = {
  'start_date': '2019-01-01',
  'end_date': '2019-03-01',
  'type_filter': 'country'
};

uiza.analytic.get_type(params)
  .then((res) => {
    //Identifier of get_total_line
  }).catch((err) => {
    //Error
  });
```

```go
import (
  "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/analytic"
)

func init() {
  Uiza.WorkspaceAPIDomain = "your-workspace-api-domain.uiza.co"
  Uiza.Authorization = "your-authorization"
}

analyticTypeFilter := uiza.AnalyticTypeFilterCountry
params := &uiza.AnalyticTypeParams{
  StartDate: uiza.String("2019-01-01"),
  EndDate: uiza.String("2019-02-28"),
  TypeFilter: &analyticTypeFilter,
}
response, err := analytic.GetType(params)
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
  var getType = UizaServices.Analytic.GetType(new AnalyticTypeParameter()
  {
    StartDate = @"2019-01-01",
    EndDate = @"2019-03-01",
    TypeFilter = TypeFilter.Country
  });

  Console.WriteLine(string.Format("Get Type Success, total record {0}", getType.Data.Count));
  Console.ReadLine();
}
catch (UizaException ex)
{
  Console.WriteLine(ex.Message);
  Console.ReadLine();
}
```

> Example Response

```json
{
    "data": [
        {
            "name": "Vietnam",
            "total_view": 15,
            "percentage_of_view": 0.625
        },
        {
            "name": "Other",
            "total_view": 9,
            "percentage_of_view": 0.375
        }
    ],
    "version": 3,
    "datetime": "2018-06-18T03:17:07.022Z",
    "policy": "public",
    "requestId": "244f6f8f-4fc5-4f20-a535-e8ea4e0cab0e",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

Get data base on 5 type of filter: **country**, **device**, **title**, **player**, **os**

**HTTP Request**

<span class="get-button"> GET </span>
```https://#{workspace_api_domain}/api/public/v3/analytic/entity/video-quality/type```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| **Authorization** | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **start_date** | *string* | Start date (UTC+0) with format: YYYY-MM-DD | **Yes** |
| **end_date** | *string* | End date (UTC+0) with format: YYYY-MM-DD | **Yes** |
| **type_filter** | *enum* | Value accept: [ **country**, **device**, **title**, **player**, **os** ] | **Yes** |


**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **name** | *string* | name of filter (can be country, device name, title, player name or os) |
| **total_view** | *number* |  Total view corresponding to filter |
| **percentage_of_view** | *number* | Percentage of view corresponding to filter |

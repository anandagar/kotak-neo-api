# **Cancel_Cover_Order**
Cancel an order

## Method 1 - Quick Method
```python
client.cancel_cover_order(order_id = "")
```

## Method 2 - Delayed Method
This method checks the order status first and then cancels the order if it is open.<br/>
```python
client.cancel_cover_order(order_id = "", isVerify=True)
```

### Example


```python
from neo_api_client import NeoAPI
from neo_api_client import BaseUrl

base_url = BaseUrl(ucc='').get_base_url()

#First initialize session and generate session token
client = NeoAPI(consumer_key="", consumer_secret="", environment='prod', access_token=None, neo_fin_key=None, base_url=base_url)
client.totp_login(mobilenumber="", ucc="", totp='')
client.totp_validate(mpin="")

try:
    # Cancel an order
    client.cancel_cover_order(order_id = "")
except Exception as e:
    print("Exception when calling OrderApi->cancel_cover_order: %s\n" % e)
```

### Parameters
| Name        | Description         | Type      |
|-------------|---------------------|-----------|
| *order_id*  | Order ID to cancel | str       | 
| *isVerify*  | Flag to check the status of order (Delayed method) | boolean   |
| *amo*       | After market order - YES, NO (optional, Default Value - NO) | str   |

### Return type

**object**

### Sample response

```json
{
    "stat": "Ok",
    "nOrdNo": "230120000017243",
    "stCode": 200
}
```

### HTTP request headers

 - **Accept**: application/json

### HTTP response details
| Status Code | Description                                  |
|-------------|----------------------------------------------|
| *200*       | Order cancelled successfully                 |
| *400*       | Invalid or missing input parameters          |
| *403*       | Invalid session, please re-login to continue |
| *429*       | Too many requests to the API                 |
| *500*       | Unexpected error                             |
| *502*       | Not able to communicate with OMS             |
| *503*       | Trade API service is unavailable             |
| *504*       | Gateway timeout, trade API is unreachable    |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints)  [[Back to README]](../README.md)

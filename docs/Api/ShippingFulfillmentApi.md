# Nopolabs\EBay\Sell\Fulfillment\ShippingFulfillmentApi

All URIs are relative to *https://api.ebay.com/sell/fulfillment/v1*

Method | HTTP request | Description
------------- | ------------- | -------------
[**createShippingFulfillment**](ShippingFulfillmentApi.md#createShippingFulfillment) | **POST** /order/{orderId}/shipping_fulfillment | Create a Shipping Fulfillment
[**getShippingFulfillment**](ShippingFulfillmentApi.md#getShippingFulfillment) | **GET** /order/{orderId}/shipping_fulfillment/{fulfillmentId} | Get a Shipping Fulfillment
[**getShippingFulfillments**](ShippingFulfillmentApi.md#getShippingFulfillments) | **GET** /order/{orderId}/shipping_fulfillment | Get Shipping Fulfillments


# **createShippingFulfillment**
> object createShippingFulfillment($order_id, $body)

Create a Shipping Fulfillment

When you group an order's line items into one or more packages, each package requires a corresponding plan for handling, addressing, and shipping; this is a shipping fulfillment. For each package, execute this call once to generate a shipping fulfillment associated with that package. Note: A single line item in an order can consist of multiple units of a purchased item, and one unit can consist of multiple parts or components. Although these components might be provided by the manufacturer in separate packaging, the seller must include all components of a given line item in the same package. Before using this call for a given package, you must determine which line items are in the package. If the package has been shipped, you should provide the date of shipment in the request. If not provided, it will default to the current date and time.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

// Configure OAuth2 access token for authorization: Authorization Code
$config = Nopolabs\EBay\Sell\Fulfillment\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

$apiInstance = new Nopolabs\EBay\Sell\Fulfillment\Api\ShippingFulfillmentApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$order_id = "order_id_example"; // string | The unique identifier of the order. This value was returned by the getOrders call in the orders.orderId field; for example, 170009092860-9849164007!140000000544476.
$body = new \Nopolabs\EBay\Sell\Fulfillment\Model\ShippingFulfillmentDetails(); // \Nopolabs\EBay\Sell\Fulfillment\Model\ShippingFulfillmentDetails | fulfillment payload

try {
    $result = $apiInstance->createShippingFulfillment($order_id, $body);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ShippingFulfillmentApi->createShippingFulfillment: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **order_id** | **string**| The unique identifier of the order. This value was returned by the getOrders call in the orders.orderId field; for example, 170009092860-9849164007!140000000544476. |
 **body** | [**\Nopolabs\EBay\Sell\Fulfillment\Model\ShippingFulfillmentDetails**](../Model/ShippingFulfillmentDetails.md)| fulfillment payload |

### Return type

**object**

### Authorization

[Authorization Code](../../README.md#Authorization Code)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getShippingFulfillment**
> \Nopolabs\EBay\Sell\Fulfillment\Model\ShippingFulfillment getShippingFulfillment($fulfillment_id, $order_id)

Get a Shipping Fulfillment

Use this call to retrieve the contents of a fulfillment based on its unique identifier, fulfillmentId (combined with the associated order's orderId). The fulfillmentId value was originally generated by the createShippingFulfillment call, and is returned by the getShippingFulfillments call in the members.fulfillmentId field.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

// Configure OAuth2 access token for authorization: Authorization Code
$config = Nopolabs\EBay\Sell\Fulfillment\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

$apiInstance = new Nopolabs\EBay\Sell\Fulfillment\Api\ShippingFulfillmentApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$fulfillment_id = "fulfillment_id_example"; // string | The unique identifier of the fulfillment. This eBay-generated value was created by the Create Shipping Fulfillment call, and returned by the getShippingFulfillments call in the fulfillments.fulfillmentId field; for example, 9405509699937003457459.
$order_id = "order_id_example"; // string | The unique identifier of the order. This value was returned by the getOrders call in the orders.orderId field; for example, 170009092860-9849164007!140000000544476.

try {
    $result = $apiInstance->getShippingFulfillment($fulfillment_id, $order_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ShippingFulfillmentApi->getShippingFulfillment: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **fulfillment_id** | **string**| The unique identifier of the fulfillment. This eBay-generated value was created by the Create Shipping Fulfillment call, and returned by the getShippingFulfillments call in the fulfillments.fulfillmentId field; for example, 9405509699937003457459. |
 **order_id** | **string**| The unique identifier of the order. This value was returned by the getOrders call in the orders.orderId field; for example, 170009092860-9849164007!140000000544476. |

### Return type

[**\Nopolabs\EBay\Sell\Fulfillment\Model\ShippingFulfillment**](../Model/ShippingFulfillment.md)

### Authorization

[Authorization Code](../../README.md#Authorization Code)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getShippingFulfillments**
> \Nopolabs\EBay\Sell\Fulfillment\Model\ShippingFulfillmentPagedCollection getShippingFulfillments($order_id)

Get Shipping Fulfillments

Use this call to retrieve the contents of all fulfillments currently defined for a specified order based on the order's unique identifier, orderId. This value is returned in the getOrders call's members.orderId field when you search for orders by creation date or shipment status.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

// Configure OAuth2 access token for authorization: Authorization Code
$config = Nopolabs\EBay\Sell\Fulfillment\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

$apiInstance = new Nopolabs\EBay\Sell\Fulfillment\Api\ShippingFulfillmentApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$order_id = "order_id_example"; // string | The unique identifier of the order. This value was returned by the getOrders call in the orders.orderId field; for example, 170009092860-9849164007!140000000544476.

try {
    $result = $apiInstance->getShippingFulfillments($order_id);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ShippingFulfillmentApi->getShippingFulfillments: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **order_id** | **string**| The unique identifier of the order. This value was returned by the getOrders call in the orders.orderId field; for example, 170009092860-9849164007!140000000544476. |

### Return type

[**\Nopolabs\EBay\Sell\Fulfillment\Model\ShippingFulfillmentPagedCollection**](../Model/ShippingFulfillmentPagedCollection.md)

### Authorization

[Authorization Code](../../README.md#Authorization Code)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)


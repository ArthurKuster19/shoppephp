# Shopee PHP Client

This is a Shopee PHP Client, currently supported for **API V2** in [ShopeeOpenPlatform](https://open.shopee.com/documents?module=87&type=2&id=64&version=2)

## Composer Install
`composer require haistar/shopee-php-sdk`

## Usage
```
$shopeeClient = new ShopApiClient();
$apiConfig = new ShopeeApiConfig();
$apiConfig->setPartnerId((int) $_ENV["SHOPEE_PARTNER_ID"]);
$apiConfig->setShopId((int) $_ENV["SHOPEE_SHOP_ID"]);
$apiConfig->setAccessToken($_ENV["SHOPEE_ACCESS_TOKEN"]);
$apiConfig->setSecretKey($_ENV["SHOPEE_SECRET_KEY"]);

$baseUrl = "https://partner.test-stable.shopeemobile.com";
$apiPath = "/api/v2/product/get_item_list";

$params = array();

$productList = $shopeeClient->httpCallGet($baseUrl, $apiPath, $params, $apiConfig);

```

## Running Test

`composer test`

For running all tests



## For laravel 8 

Run `composer require haistar/shopee-php-sdk`

Then `composer update`

Add this to .Env

`SHOPEE_PARTNER_ID={partner_id}`
`SHOPEE_SHOP_ID= {shop_id}`
`SHOPEE_ACCESS_TOKEN={access_token}`
`SHOPEE_SECRET_KEY={partner_key}`



Add ontop of Controller

`use Haistar\ShopeePhpSdk\request\shop\ShopApiClient;`
`use Haistar\ShopeePhpSdk\client\ShopeeApiConfig;`


Try

```
public function index()
{

$shopeeClient = new ShopApiClient();
$apiConfig = new ShopeeApiConfig();
$apiConfig->setPartnerId((int) $_ENV["SHOPEE_PARTNER_ID"]);
$apiConfig->setShopId((int) $_ENV["SHOPEE_SHOP_ID"]);
$apiConfig->setAccessToken($_ENV["SHOPEE_ACCESS_TOKEN"]);
$apiConfig->setSecretKey($_ENV["SHOPEE_SECRET_KEY"]);

$baseUrl = "https://partner.test-stable.shopeemobile.com";
$apiPath = "/api/v2/product/get_item_list";

$params = ["offset"=>0,"item_status"=>"NORMAL","page_size" => 10,];

$productList = $shopeeClient->httpCallGet($baseUrl, $apiPath, $params, $apiConfig);

return response()->json($productList);


 }
```
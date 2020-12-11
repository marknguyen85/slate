---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell: cURL
  - php: PHP - cURL
  - javascript: JavaScript - Fetch

toc_footers:
  - <a href='https://seller.geargag.com/dev/stores'>Sign Up for a Developer Key</a>
  - <a href='https://geargag.com'>Documentation Powered by GearGag</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Overview

The GearGag API is organized around REST. Our API accepts JSON request payload and returns JSON-encoded responses,
and uses standard HTTP response codes, authentication, and verbs.

# Authentication
The API uses Access Token to authenticate requests. Authentication to the API is performed via Token.
Your Access Token carry many privileges, so be sure to keep them secure!
Do not share your secret Access Token in publicly accessible areas such as GitHub, client-side code, and so forth.
If you are currently logged in account settings, you can go to <a href="https://seller.geargag.com/dev/stores">[Stores Access Token]</a> and get API token there.

> To authorize, use this code:

```shell
curl --location --request POST 'URL_PLACE_HERE' \
--header 'Authorization: REPLACE_YOUR_TOKEN_HERE' \
--header 'Content-Type: application/json'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'URL_PLACE_HERE',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST/GET',
  CURLOPT_POSTFIELDS =>'{
	"sku":""
}',
  CURLOPT_HTTPHEADER => array(
    'Authorization: REPLACE_YOUR_TOKEN_HERE',
    'Content-Type: application/json',
  ),
));

$response = curl_exec($curl);

curl_close($curl);
// TODO Something
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "REPLACE_YOUR_TOKEN_HERE");
myHeaders.append("Content-Type", "application/json");

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: {},
  redirect: 'follow'
};

fetch("URL_PLACE_HERE", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Make sure to replace `REPLACE_YOUR_TOKEN_HERE` with your API key.

GearGag uses API token to allow access to the API. You can get a new API token at [Stores Access Token](https://seller.geargag.com/dev/stores).

GearGag expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: REPLACE_YOUR_TOKEN_HERE`

<aside class="notice">
You must replace <code>REPLACE_YOUR_TOKEN_HERE</code> with your personal API token.
</aside>

# Product

## Search dimension by Sku

```shell
curl --location --request POST 'https://api.geargag.com/integrate/sku.json' \
--header 'Authorization: REPLACE_YOUR_TOKEN_HERE' \
--header 'Content-Type: application/json' \
--data-raw '{
	"sku":""
}'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://api.geargag.com/integrate/sku.json',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS =>'{
	"sku":""
}',
  CURLOPT_HTTPHEADER => array(
    'Authorization: REPLACE_YOUR_TOKEN_HERE',
    'Content-Type: application/json',
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "REPLACE_YOUR_TOKEN_HERE");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({"sku":""});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.geargag.com/integrate/sku.json", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
  "status": true,
  "data": [
    {
      "id": "5346",
      "name": "Front",
      "id_catalog": "128",
      "dimensions": [
        "4500x5400",
        "2400x3000",
        "2100x2400",
        "2400x3200",
        "2800x3200",
        "4200x4800"
      ]
    }
  ]
}
```

Returns formatted dimensions GearGag supports by sku.

### HTTP Request

`POST https://api.geargag.com/integrate/sku.json`

### Request (json):

Name | Required | Type | Description
--------- | ------- | ----------- | --------------------------
sku | Yes | String | The Sku of product
&nbsp;|&nbsp;|&nbsp;|<img width=1000/>

### Response (json):

Name | Type | Description
--------- | ------- | --------------------------
status | String | true/false
message | String | 
[data](#product_data) | jsonArray |<img width=1000/>

<ins>data</ins><a name="product_data"></a>: The data is an array of

Name | Type | Description
--------- | ------- | --------------
id | Integer | The Item ID
name | String | The Item name, ex: "Front"
id_catalog | Integer | The category ID of item
dimensions | stringArray | a list dimensions ex: ["4500x5400", "2400x3000"]
&nbsp;|&nbsp;|<img width=1000/>

## Get all sku of supported catalog

```shell
curl --location --request GET 'https://api.geargag.com/integrate/sku.json' \
--header 'Authorization: REPLACE_YOUR_TOKEN_HERE' \
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://api.geargag.com/integrate/sku.json',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'GET',
  CURLOPT_HTTPHEADER => array(
    'Authorization: REPLACE_YOUR_TOKEN_HERE',
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;

```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "REPLACE_YOUR_TOKEN_HERE");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://api.geargag.com/integrate/sku.json", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
    "status": true,
    "data": [
        {
            "id": "128",
            "name": "Guys Tee",
            "sku": "GUYSTEE-BLACK-L-FRONT",
            "category": "Apparel",
            "attributes": {
                "Color": "Black",
                "Size": "L",
                "Side": "Front"
            }
        },
        {
            "id": "129",
            "name": "Guys Tee",
            "sku": "GUYSTEE-BLACK-M-FRONT",
            "category": "Apparel",
            "attributes": {
                "Color": "Black",
                "Size": "M",
                "Side": "Front"
            }
        },
        {
            "id": "130",
            "name": "Guys Tee",
            "sku": "GUYSTEE-BLACK-S-FRONT",
            "category": "Apparel",
            "attributes": {
                "Color": "Black",
                "Size": "S",
                "Side": "Front"
            }
        }
    ]
}
```

Returns all sku of supported catalog.

### HTTP Request

`GET https://api.geargag.com/integrate/sku.json`

### Request (json):

Not required

### Response (json):

Name | Type | Description
--------- | ------- | --------------------------
status | String | true/false
message | String |
[data](#all_sku_data) | jsonArray |<img width=1000/>

<ins>data</ins><a name="all_sku_data"></a>: The data is an array of

Name | Type | Description
--------- | ------- | --------------
id | Integer | Item's ID
name | String | Item's name
sku | String | Item's SKU
category | String | The category of item
[attributes](#all_sku_attributes) | object | Item's attributes
&nbsp;|&nbsp;|<img width=1000/>

<ins>attributes</ins><a name="all_sku_attributes"></a>

Name | Type | Description
--------- | ------- | --------------
Color | String | Item's color
Size | String | Item's size
Side | String | Item's side (Front/Back)
&nbsp;|&nbsp;|<img width=1000/>

# Order

## Create an Order

```shell
curl --location --request POST 'https://api.geargag.com/integrate/order.json' \
--header 'Authorization: REPLACE_YOUR_TOKEN_HERE' \
--header 'Content-Type: application/json' \
--data-raw '{
    "order_id": "AM-123",
    "shipping_info": {
        "full_name": "John",
        "address_1": "Jennifer",
        "address_2": "",
        "city": "California",
        "state": "CA",
        "postcode": "12345",
        "country": "US",
        "email": "customer@example.com",
        "phone": "0123456789"
    },
    "items": [
        {
            "name": "Example product",
            "sku_external": "Geargag example",
            "sku": "GUYSTEE-BLACK-L-0",
            "quantity": 1,
            "price": 22.99,
            "currency": "USD",
            "import_mockup_1": "https://shark.nyc3.digitaloceanspaces.com/2020/5/8/1585018074858-0814234699-Unisex-black-front.jpg",
            "import_mockup_2": "",
            "import_mockup_3": "",
            "dimensions": [
                {
                    "name": "Front",
                    "image_code": "5F6AE6C167E48"
                },
                {
                    "name": "Back",
                    "image_code": "5F6AE6C167E48"
                }
            ]
        }
    ]
}'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://api.geargag.com/integrate/order.json',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS =>'{
    "order_id": "AM-123",
    "shipping_info": {
        "full_name": "John",
        "address_1": "Jennifer",
        "address_2": "",
        "city": "California",
        "state": "CA",
        "postcode": "12345",
        "country": "US",
        "email": "customer@example.com",
        "phone": "0123456789"
    },
    "items": [
        {
            "name": "Example product",
            "sku_external": "Geargag example",
            "sku": "GUYSTEE-BLACK-L-0",
            "quantity": 1,
            "price": 22.99,
            "currency": "USD",
            "import_mockup_1": "https://shark.nyc3.digitaloceanspaces.com/2020/5/8/1585018074858-0814234699-Unisex-black-front.jpg",
            "import_mockup_2": "",
            "import_mockup_3": "",
            "dimensions": [
                {
                    "name": "Front",
                    "image_code": "5F6AE6C167E48"
                },
                {
                    "name": "Back",
                    "image_code": "5F6AE6C167E48"
                }
            ]
        }
    ]
}',
  CURLOPT_HTTPHEADER => array(
    'Authorization: REPLACE_YOUR_TOKEN_HERE',
    'Content-Type: application/json',
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;

```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "REPLACE_YOUR_TOKEN_HERE");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({"order_id":"AM-123","shipping_info":{"full_name":"John","address_1":"Jennifer","address_2":"","city":"California","state":"CA","postcode":"12345","country":"US","email":"customer@example.com","phone":"0123456789"},"items":[{"name":"Example product","sku_external":"Geargag example","sku":"GUYSTEE-BLACK-L-0","quantity":1,"price":22.99,"currency":"USD","import_mockup_1":"https://shark.nyc3.digitaloceanspaces.com/2020/5/8/1585018074858-0814234699-Unisex-black-front.jpg","import_mockup_2":"","import_mockup_3":"","dimensions":[{"name":"Front","image_code":"5F6AE6C167E48"},{"name":"Back","image_code":"5F6AE6C167E48"}]}]});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.geargag.com/integrate/order.json", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
    "status": true,
    "message": "Order has been created",
    "data": {
        "order_id": 666666
    }
}
```

You can use Geargag Order API to import orders to your Geargag store and request fulfillment for these orders.

### HTTP Request

`POST https://api.geargag.com/integrate/order.json`

### Request (json):

Name | Required | Type | Description
--------- | -------- | -------- | --------------------------
order_id | Yes | String | The Order number in your system. Use this order number to retrieve tracking number subsequently.
[shipping_info](#shipping_info) | Yes | Object|Shipping address of the order.
[items](#items) | Yes | String | An array of product items.
&nbsp;|&nbsp;|&nbsp;|<img width=1000/>

<ins>shipping_info</ins><a name="shipping_info"></a>

Name | Required | Type | Description
--------- | -------- | -------- | --------------------------
full_name | Yes | String | The customer name.
address_1 | Yes |	String |	The customer address.
address_2 |	No | String |	The customer address 2.
city |	No |	String | The city name.
state |	Yes | String | The state code.
postcode |	No |	String |	The PostCode.
country | Yes |	String |	The country code.
email |	No |	String |	The customer email.
phone |	Yes |	String |	The customer phone.
&nbsp;|&nbsp;|&nbsp;|<img width=1000/>


<ins>items</ins><a name="items"></a>: The items is an array of

Name | Required | Type | Description
--------- | -------- | -------- | --------------------------
name |	Yes |	String |	Title of product item.
sku_external |	Yes |	String |	Sku_external is a unique string used to recognize your unique design for unique type of product. You can name your sku_external without limited ideas, however, be careful when you updating a existing sku_external with different designs & a new type of product, the previous unfulfilled orders or new synced orders with the same sku_external will be changed too.
sku |	Yes |	String |	The SKU of product item.
price |	Yes |	String |	Price of product item. Use this value to take advance of Geargag statistics feature.
currency |	Yes |	String |	The currency of product item price.
quantity |	Yes |	Integer |	The number of product items.
[dimensions](#dimensions) |	Yes |	Object |	The detailed dimensions of product item.
import_mockup_1 |	No |	URL |	(Link url of mockup 1)
import_mockup_2 |	No |	URL |	(Link url of mockup 2)
import_mockup_3 |	No |	URL |	(Link url of mockup 3)
&nbsp;|&nbsp;|&nbsp;|<img width=1000/>


<ins>dimensions</ins><a name="dimensions"></a>: The dimensions is an array of

Name | Required | Type | Description
--------- | -------- | -------- | --------------------------
name |	Yes |	String |	Applicable for some special products. For example, possible values: "Front" or "Back".
image_code |	Yes |	String |	The Image code.
&nbsp;|&nbsp;|&nbsp;|<img width=1000/>

### Response (json):

Name | Type | Description
--------- | ------- | --------------------------
status | String | true/false
message | String |
[data](#order_data) | jsonObject |<img width=1000/>

<ins>data</ins><a name="order_data"></a>

Name | Type | Description
--------- | ------- | --------------
order_id | Integer | The ID of created GearGag order
&nbsp;|&nbsp;|&nbsp;|<img width=1000/>

## Get Order Tracking

```shell
curl --location --request GET 'https://api.geargag.com/integrate/tracking.json?order_id=AM-123&type=1' \
--header 'Authorization: REPLACE_YOUR_TOKEN_HERE' \
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://api.geargag.com/integrate/tracking.json?order_id=AM-123&type=1',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'GET',
  CURLOPT_HTTPHEADER => array(
    'Authorization: REPLACE_YOUR_TOKEN_HERE',
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;

```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "REPLACE_YOUR_TOKEN_HERE");
myHeaders.append("Cookie", "__cfduid=d7bbd89652c29213f4b98d1581daa6a4d1607401176");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://api.geargag.com/integrate/tracking.json?order_id=AM-123&type=1", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
    "status": true,
    "message": "Order has been created",
    "data": {
      "order_id": 666666,
      "order_id_import": "AM-123",
      "tracking_code": "123456789",
      "sku": "123456",
      "name": "xxxx"
    }
}
```

You can get order tracking after order was fulfilled by two ways which are by `order_id`.

### HTTP Request

`GET https://api.geargag.com/integrate/tracking.json`

### Request Params:

Name | Required | Type | Description
--------- | -------- | -------- | --------------------------
order_id | Yes | Integer | GearGag OrderID
type | No | Integer | If type IS NULL or type = 1 then order_id exists on the system. If type = 2 then order_id that imported manual by customer
&nbsp;|&nbsp;|&nbsp;|<img width=1000/>

### Response (json):

Name | Type | Description
--------- | ------- | --------------------------
status | String | true/false
message | String |
[data](#tracking_data) | jsonObject |<img width=1000/>

<ins>data</ins><a name="tracking_data"></a>

Name | Type | Description
--------- | ------- | --------------
order_id | Integer | The ID of order
order_id_import | Integer | The ID of imported order
tracking_code | String | The code of tracking
sku | Integer | The SKU of product
name | Integer | The name of product
&nbsp;|&nbsp;|&nbsp;|<img width=1000/>

# Resources

## Upload file to library

```shell
curl --location --request POST 'https://api.geargag.com/integrate/image.json' \
--header 'Authorization: REPLACE_YOUR_TOKEN_HERE' \
--form 'file=@"./GearGag/capture.png"' \
--form 'code="TT123456"'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://api.geargag.com/integrate/image.json',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS => array('file'=> new CURLFILE('./GearGag/capture.png'),'code' => 'TT123456'),
  CURLOPT_HTTPHEADER => array(
    'Authorization: REPLACE_YOUR_TOKEN_HERE',
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;

```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "REPLACE_YOUR_TOKEN_HERE");

var formdata = new FormData();
formdata.append("file", fileInput.files[0], "./GearGag/capture.png");
formdata.append("code", "TT123456");

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: formdata,
  redirect: 'follow'
};

fetch("https://api.geargag.com/integrate/image.json", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
    "status": true,
    "message": "Success",
    "data": {
        "id_shop": 666666,
        "type": "artwork",
        "name": "capture.png",
        "code": "TT123456",
        "tag": "",
        "mime_type": "image/png",
        "hash": "",
        "cdn": "a7",
        "size": 1442,
        "file": "https://pixillum.com/pro/IFkUOy0xwnLtXA4gRt7u2w/library/666666/4387/origin/666666_5fd09f5b79b1d.png",
        "note": "File is an image - image/png.",
        "width": 263,
        "height": 151,
        "created_at": "2020-12-09 01:56:45",
        "file_thumb": "https://pixillum.com/pro/IFkUOy0xwnLtXA4gRt7u2w/library/666666/4387/thumb/666666_5fd09f5b79b1d.png"
    }
}
```

Geargag support file format extension ['gif', 'png', 'jpg', 'jpeg', 'svg', 'ttf', 'ai'].

### HTTP Request

`POST https://api.geargag.com/integrate/image.json`

### Request (form-data):

Name | Required | Type | Description
--------- | -------- | -------- | --------------------------
file | Yes	| File	| The File data.
code	| Yes	| String	| Code image of library *If code is null, code auto generate from name your file. Don't input special characters ('^£$%&*()}{@#~?><>,|=_+¬-)

### Response (json):

Name | Type | Description
--------- | ------- | --------------------------
status | String | true/false
message |	String | [Image has been uploaded]
[data](#upload_image_data) | Object |<img width=1000/>

<ins>data</ins><a name="upload_image_data"></a>

Name | Type | Description
--------- | ------- | --------------------------
name	| String	| The name of image
code	| String	| The code of image
mime_type	| String	| The image mine type
size	| Integer	| The image size
note	| String	| The image note
width	| Integer	| The image with
height	| Integer	| The image height
created_at	| Date	| The created date
file	| URL	| The URL of image
file_thumb	| URL	| The URL of thumb image
data | jsonObject |<img width=1000/>

## Search library by code image

```shell
curl --location --request POST 'https://api.geargag.com/integrate/library.json' \
--header 'Authorization: REPLACE_YOUR_TOKEN_HERE' \
--header 'Content-Type: application/json' \
--data-raw '{
	"code":"TT123456"
}'
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://api.geargag.com/integrate/library.json',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS =>'{
	"code":"TT123456"
}',
  CURLOPT_HTTPHEADER => array(
    'Authorization: REPLACE_YOUR_TOKEN_HERE',
    'Content-Type: application/json',
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "REPLACE_YOUR_TOKEN_HERE");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({"code":"TT123456"});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.geargag.com/integrate/library.json", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
    "status": true,
    "data": {
        "code": "xxxxx",
        "type": "artwork",
        "width": "263",
        "height": "151",
        "file": "/library/xxxxx/4387/origin/xxxxx_5fd09f5b79b1d.png",
    }
}
```

Returns an image's information from library by `code`.

### HTTP Request

`POST https://api.geargag.com/integrate/library.json`

### Request (json):

Name | Required | Type | Description
--------- | ------- | ----------- | --------------------------
code | Yes | String | The Code of image
&nbsp;|&nbsp;|&nbsp;|<img width=1000/>

### Response (json):

Name | Type | Description
--------- | ------- | --------------------------
status | String | true/false
message | String | 
[data](#library_data) | Object |<img width=1000/>

<ins>data</ins><a name="library_data"></a>

Name | Type | Description
--------- | ------- | --------------------------
code	| String	| The code of image
type	| String	| The type of image
width	| Integer	| The image with
height | Integer	| The image height
file	| URL	| The URL of image
&nbsp;|&nbsp;|<img width=1000/>

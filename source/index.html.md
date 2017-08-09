---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:

includes:
  - errors

search: true
---

# Introduction

Welcome to the Happy Shop API! You can use our API to access Happy Shop API endpoints, which can get information on different products in our database.

We have language bindings in Shell! You can view code examples in the dark area to the right.

# Products

## Get All Products

```shell
curl "http://happpy-shop.herokuapp.com/api/v1/products"
```

> The above command returns JSON structured like this:

```json
{
   "data": [
      {
         "id": "1",
         "type": "products",
         "links": {
            "self": "http://happpy-shop.herokuapp.com/api/v1/products/1"
         },
         "attributes": {
            "name": "Output Tuner",
            "sold-out": false,
            "category": "tools",
            "under-sale": false,
            "price": 70193,
            "sale-price": null,
            "sale-text": null
         }
      },
      {
         "id": "2",
         "type": "products",
         "links": {
            "self": "http://happpy-shop.herokuapp.com/api/v1/products/2"
         },
         "attributes": {
            "name": "Side Filter",
            "sold-out": false,
            "category": "tools",
            "under-sale": true,
            "price": 20000,
            "sale-price": 10000,
            "sale-text": "50% OFF"
         }
      },
   ],
   "links": {
      "first": "http://happpy-shop.herokuapp.com/api/v1/products?page%5Bnumber%5D=1&page%5Bsize%5D=10",
      "next": "http://happpy-shop.herokuapp.com/api/v1/products?page%5Bnumber%5D=2&page%5Bsize%5D=10",
      "last": "http://happpy-shop.herokuapp.com/api/v1/products?page%5Bnumber%5D=3&page%5Bsize%5D=10"
   }
}
```

This endpoint retrieves all products.

### HTTP Request

`GET http://happpy-shop.herokuapp.com/api/v1/products`

### Query Parameters

Parameter | Example Value | Description
--------- | ------- | -----------
filter[category] | makeup | Filter products by category.
filter[min_price] | 100 | Filter products by minimum price.
filter[max_price] | 2000 | Filter products by maximum price.
sort | price | Sort products by attribute depending on the prefix (- for descending; no prefix if ascending).
page[size] | 6 | The number of products per page. Default is 10.
page[number] | 6 | Paginate products by page number.

<aside class="success">
Note - product price attribute value is set as integer. In actual currency, 10000 is equal to 100.00.
</aside>

## Get a Specific Product

```shell
curl "http://happpy-shop.herokuapp.com/api/v1/products/1"
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "id": "1",
        "type": "products",
        "links": {
            "self": "http://happpy-shop.herokuapp.com/api/v1/products/1"
        },
        "attributes": {
            "name": "Output Tuner",
            "sold-out": false,
            "category": "tools",
            "under-sale": false,
            "price": 70193,
            "sale-price": null,
            "sale-text": null
        }
    }
}
```

This endpoint retrieves a specific product.

### HTTP Request

  `GET http://happpy-shop.herokuapp.com/api/v1/products/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the product to retrieve

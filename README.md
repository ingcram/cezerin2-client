# Cezerin API client library

Allows asynchronous requests to Cezerin REST API and get results with Promise.

Install with:

    npm install cezerin-client


## Usage

```javascript
let api = require('cezerin-client');
api.init('https://website.com/api/', '<token>');

// get all categories
api.product_categories.list().then(({status, json}) => {
    console.log(json[0].name)
});

// create a category
api.product_categories.create({name: 'Woman', active: false})
.then(({status, json}) => {
    console.log(`New id: ${json.id}`)
});
```

##  Error Handling

```javascript
let api = require('cezerin-client');
api.init('https://website.com/api/', '<token>');

api.product_categories.create({ name: 'Woman', active: false })
.then(({status, json}) => {
  if(status === 200) {
    return json;
  } else {
    throw 'Error';
  }
})
.catch(error => {
    console.log(error)
});
```

## Methods

* `init(baseUrl, token)`
* `authorize(baseUrl, user, pass)`
* `sitemap.list()`
* `sitemap.retrieve(path)`
* `product_categories.list()`
* `product_categories.retrieve(id)`
* `product_categories.create(data)`
* `product_categories.update(id, data)`
* `product_categories.delete(id)`
* `product_categories.uploadImage(data)`
* `product_categories.deleteImage(id)`
* `products.list({
    - offset: 0,
    - limit: 10,
    - fields: 'id, name, price',
    - brand_id: '<id>',
    - category_id: '<id>',
    - active: true,
    - discontinued: false,
    - search: '',
    - on_sale: true,
    - stock_status: 'available',
    - price_from: 0,
    - price_to: 100,
    - sku: '',
    - ids: '<id>,<id>,<id>',
    - sort: 'regular_price,-stock_quantity',
    - currency: 'USD'
   })`
* `products.retrieve(id)`
* `products.retrieve(id, { currency: 'USD' })`
* `products.create(data)`
* `products.update(id, data)`
* `products.delete(id)`
* `products.uploadImage(productId, data)`
* `products.deleteImage(productId, imageId)`
* `themes.exportCurrent()`
* `themes.importAndInstall(formData)`
* `customers.list`
* `customers.retrieve`
* `customers.create`
* `customers.update`
* `customers.delete`
* `customer_groups.list`
* `customer_groups.retrieve`
* `customer_groups.create`
* `customer_groups.update`
* `customer_groups.delete`

## Contributing

If you can, please contribute by reporting issues, discussing ideas, or submitting pull requests with patches and new features. We do our best to respond to all issues and pull requests within a day or two, and make patch releases to npm regularly.
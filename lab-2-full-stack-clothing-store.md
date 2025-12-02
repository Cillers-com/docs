---
description: >-
  Applying similar methods as we did in previous lab, we will create a
  full-stack clothing store website which allows us to place orders, with
  workflows managed in temporal.
hidden: true
---

# Lab 2: Full Stack Clothing Store

## 1. Setup

Before proceeding, make sure you are sitting in a new, empty directory, which we will create our project in. Then, open the Bluetext extension from the activity bar on the left. You will have the option to preform a quick setup which configures your workspace for working with Bluetext and Polytope. Run this quick setup and make sure to select "Cline (Recommended)" when asked which coding agent you want to configure.&#x20;

Now, a polytope.yml file has been created at the root of your directory which exposes polytope to bluetext's tools, and Cline has been configured to connect to Polytopes MCP server.





* Run all the tools, and create models for order, customer, product



Customer fields:



```python
    # Document fields
    id: UUID  # Primary key - required
    name: str
    email: str 
    total_loyalty_points: int
    created_at: datetime
```

Order fields:

```python
 # Document fields
    id: UUID  # Primary key - required
    customer_id: UUID
    product_id: int 
    variant_id: int 
    quantity: int 
    unit_price: int 
    total_price: int 
    points_to_award: int 
    status: str 
    returned_at: Optional[datetime]
    points_awarded: bool
    points_awarded_at: Optional[datetime]
    workflow_id: str
    created_at: datetime
```

Import Couchbase\ THESE ARE FIELDS FOR CLOTHES

```
# Document fields
    id: UUID  # Primary key - required
    product_id: int
    product_number: str
    product_name: str
    brand: str
    recommended_retail_price: str
    country_of_origin: str
    department: str
    product_group: str
    product_group2: Optional[str]
    product_type: str
    external_material: Optional[str]
    internal_material: Optional[str]
    sole_material: Optional[str]
    silhouette: Optional[str]
    function: Optional[str]
    color: Optional[str]
    image_urls: list[str]
    variants: list[Variant]
```

from the couchbase UI, import the couchbase document and prompt agent with the following:<br>

{% code overflow="wrap" %}
````
I have a fullstack app up and running through Polytope. You can interact with it through mcp tools. For the API I created models for Orders, Customers and Products. Products do not yet have fields defined. Create fields in accordance to my database entries. Below is an example for a product entry in the couchbase db:

```
{ "product_id": 3101524, "product_number": "61254-77", "product_name": "Osaka Camo Hw Hood Camo", "brand": "Primitive Skateboarding", "recommended_retail_price": "1229", "country_of_origin": "cn", "department": "men", "product_group": "hoodies and sweatshirts", "product_group2": "hoodies", "product_type": "apparel", "external_material": null, "internal_material": null, "sole_material": null, "silhouette": null, "function": null, "color": "multicolor", "image_urls": [ "https://images.footway.com/02/61254-77_001.png", "https://images.footway.com/02/61254-77_002.png", "https://images.footway.com/02/61254-77_003.png" ], "variants": [ { "variant_id": 3101223, "variant_number": "261254770044", "ean": "0194942352553", "size": "S", "lengthMilliMeter": 300, "widthMilliMeter": 250, "heightMilliMeter": 40, "volumeMilliMeterCubed": 3000000, "weightGram": 500 }, { "variant_id": 3101224, "variant_number": "261254770037", "ean": "0194942352546", "size": "M", "lengthMilliMeter": 300, "widthMilliMeter": 250, "heightMilliMeter": 40, "volumeMilliMeterCubed": 3000000, "weightGram": 500 }, { "variant_id": 3101222, "variant_number": "261254770020", "ean": "0194942352539", "size": "L", "lengthMilliMeter": 300, "widthMilliMeter": 250, "heightMilliMeter": 40, "volumeMilliMeterCubed": 3000000, "weightGram": 500 }, { "variant_id": 3101225, "variant_number": "261254770013", "ean": "0194942352560", "size": "XL", "lengthMilliMeter": 300, "widthMilliMeter": 250, "heightMilliMeter": 40, "volumeMilliMeterCubed": 3000000, "weightGram": 500 }, { "variant_id": 3101140, "variant_number": "261254770006", "ean": "0194942352577", "size": "XXL", "lengthMilliMeter": 300, "widthMilliMeter": 250, "heightMilliMeter": 40, "volumeMilliMeterCubed": 3000000, "weightGram": 500 } ] }
````
{% endcode %}

API:

## Prompt 2

Lets refresh the context and create some endpoints to handle the interactions we want to support in our app.

Customer Routes POST /customers - Create new customer GET /customers/{customer\_id} - Get customer by ID (includes total\_loyalty\_points) GET /customers - List all customers (with pagination) GET /customers/{customer\_id}/orders - Get customer's order history

Product Routes GET /products/{product\_id} - Get product by ID GET /products - List all products (with pagination, filtering by department/group)

Order Routes POST /orders - Create new order (triggers Temporal workflow) GET /orders/{order\_id} - Get order by ID GET /orders - List all orders (with pagination, filtering by customer) POST /orders/{order\_id}/return - Request return (must be within 30 seconds of order\_date)

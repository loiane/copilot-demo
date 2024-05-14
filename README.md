# API Documentation for Products Endpoint

## GET /api/products

This endpoint returns a list of all available products in the system.

### Response Format

The response is formatted as JSON and includes an array of products. Each product object contains the following information:

- `id`: Unique product ID (Long)
- `name`: Name of the product (String, 3-100 characters)
- `description`: Brief summary of the product (String, 0-500 characters, optional)
- `price`: Price of the product (BigDecimal)

### Example Response

```json
[
  {
    "id": 12345,
    "name": "Awesome T-Shirt",
    "description": "The most comfortable t-shirt you'll ever wear.",
    "price": 19.99
  },
  {
    "id": 54321,
    "name": "Stylish Jeans",
    "description": "Classic denim jeans with a modern fit.",
    "price": 49.99
  }
]
```

### Additional Notes

- The API uses Hibernate validation for request parameters.
- The API follows a package-by-domain organization, including a Controller layer, a Service layer, model, and repository.

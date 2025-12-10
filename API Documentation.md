Chosen API Endpoint:

For this task, I decided to document the Product API built with JavaScript and Express. I focused on the two GET routes that fetch product data. These endpoints are useful because they show how filtering, pagination, and error handling work in real API environments.

Prompt 1 Application: Comprehensive Endpoint Documentation
GET /api/products — List Products with Filtering and Pagination

Purpose:
Returns a paginated list of products with several filtering and sorting options.

Query Parameters:
- category: Filter by category
- minPrice / maxPrice: Set a price range
- sort: Field to sort by, default createdAt
- order: Sorting direction, asc or desc (default)
- page: Page number (default 1)
- limit: Items per page (default 20, max 100)
- inStock: Only return items in stock

{
  "products": [
    {
      "_id": "61fa9bcf5c130b2e6d675432",
      "name": "Wireless Headphones",
      "description": "High-quality wireless headphones with noise cancellation",
      "price": 89.99,
      "category": "electronics",
      "stockQuantity": 45,
      "createdAt": "2023-02-01T15:32:47Z",
      "updatedAt": "2023-03-15T09:21:08Z"
    }
  ],
  "pagination": {
    "total": 42,
    "page": 1,
    "limit": 20,
    "pages": 3
  }
}

Errors:
- 500 – Server issue

Examples:
- Get all products:
    - GET /api/products

Filter by category:
- GET /api/products?category=electronics&limit=10


GET /api/products/:productId — Retrieve a Single Product

What it does:
- Returns details for one product using its ID.

Path Parameter:
- productId (string, required)

{
  "_id": "61fa9bcf5c130b2e6d675432",
  "name": "Wireless Headphones",
  "description": "High-quality wireless headphones with noise cancellation",
  "price": 89.99,
  "category": "electronics",
  "stockQuantity": 45,
  "createdAt": "2023-02-01T15:32:47Z",
  "updatedAt": "2023-03-15T09:21:08Z"
}

Errors:
- 400 – Invalid ID format
- 404 – Product not found
- 500 – Server error


Reflection

This exercise showed me how much clarity and structure matter in API documentation. The biggest challenge was balancing thoroughness with readability. Writing for actual developers helped me shape the tone and examples.

I found that including both Markdown-style docs and a formal OpenAPI spec covers two different audiences:
- Developers who want clear explanations
- Tools that need structured definitions

Overall, the process reinforced how important good documentation is when designing and building APIs.
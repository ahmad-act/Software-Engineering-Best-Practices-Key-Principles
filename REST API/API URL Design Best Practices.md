## 🌐 API URL Design Best Practices

### 1. URL Structure & Formatting

#### a) Use lowercase letters in URLs
```http
✅ GET /users/:userId/orders
❎ GET /Products
```
**Why?**
- URLs are case-sensitive, and using lowercase ensures consistency.
- Avoids issues in case-sensitive file systems and environments.

#### b) Use hyphen, not underscore for resource names
```http
✅ PUT /user-posts/:postId
❎ PUT /user_posts/:postId
```
**Why?**
- Hyphens improve readability in URLs.
- Avoids confusion, as underscores can be mistaken for spaces.

### 2. Resource Naming

#### a) Use noun for resource names, not verbs
```http
✅ POST /products
❎ POST /createProduct
```
**Why?**
- Resources should represent entities (nouns), not actions (verbs).
- HTTP methods (GET, POST, PUT, DELETE) already define actions.

#### b) Use plural to denote a resource for collections
```http
✅ GET /products
✅ GET /orders/:orderId
✅ GET /users/:userId/pictures
```
**Why?**
- Plural nouns indicate collections.
- Maintains consistency across endpoints.

#### c) Use singular for single resource
```http
✅ GET /users/:userId/cart
```
**Why?**
- Represents a unique entity for a user (e.g., a shopping cart).

### 3. Variables & Path Parameters

#### a) Use camel case for variables in Path Parameters and Query Strings
```http
✅ GET /products/:productId
❎ GET /products/:ProductID
```
**Why?**
- Consistent variable naming across APIs.
- Improves readability and maintains best practices for JSON payloads.

#### b) Clearly represent relationships between resources in URLs
```http
✅ GET /users/{userId}/orders/{orderId}
✅ GET /products/{productId}/reviews
```
**Why?**
- Clarifies resource relationships.
- Keeps the structure intuitive.

### 4. Actions & Non-CRUD Operations

#### a) No CRUD names/verbs in URLs
```http
✅ POST /products
❎ POST /products/create
✅ GET /orders/:orderId
❎ GET /orders/:orderId/getDetails
✅ DELETE /comments/:commentId
❎ DELETE /comments/:commentId/remove
```
**Why?**
- HTTP methods already define the action.
- Keeps URLs clean and concise.

#### b) Use HTTP methods for CRUD
```http
✅ POST /products
✅ PUT /products/:id
✅ PATCH /products/:id
✅ DELETE /products/:id
```
**Why?**
- Follows REST principles.
- Avoids redundant or unclear action names.

#### c) Use verbs for specific actions that are not standard CRUD operations
```http
✅ PATCH /orders/:orderId/cancel
✅ GET /products/:productId/reviews
✅ GET /users/:userId/cart
✅ GET /users/:userId/cart/checkout
```
**Why?**
- Some actions don’t fit into CRUD operations and need explicit verbs.
- Improves clarity and maintainability.

#### d) Verbs for custom/additional actions
```http
✅ POST /orders/:orderId/cancel
✅ POST /users/:userId/cart/checkout
❎ GET /users/:userId/cart/checkout
```
**Why?**
- POST, PUT, PATCH, and DELETE are used for actions that change the state.
- GET should only retrieve information.

### 5. Filtering, Sorting, & Pagination

#### a) Use query string for filtering, sorting & pagination
```http
✅ GET /products?varient=red&size=small
✅ GET /pictures?page=2&size=20
✅ GET /post?search=react&sort=created&order=asc
```
**Why?**
- Keeps URLs clean and structured for filtering and sorting.

#### b) Use query parameters
```http
Filtering:
✅ GET /products?category=electronics&color=red
Sorting:
✅ GET /products?sort=price&order=desc
Pagination:
✅ GET /products?page=2&limit=20
```
**Why?**
- Query parameters are scalable and flexible.
- Keeps URLs concise and readable.

#### c) Standardize parameter names
Use `page`, `limit`, `sort`, `filter`, `q` (search query).
**Why?**
- Maintains consistency across APIs.
- Developers can easily understand and use query parameters.

### 6. Versioning

#### a) Always use versioning (v1, v2; not v1.2)
```http
✅ GET /api/v1/posts
✅ DELETE /api/v2/comments/:commentedId
```
**Why?**
- Allows APIs to evolve while maintaining backward compatibility.

#### b) Major versions in URLs
```http
✅ GET /api/v1/posts
❎ GET /api/v1.2/posts
```
**Why?**
- Minor versions (v1.2) can cause unexpected breaking changes.
- Use headers for minor versioning (e.g., `Accept: application/vnd.myapi.v1+json`).

### 7. Relationships & Nesting

#### a) Limit nesting depth (max 2–3 levels)
```http
✅ GET /users/:userId/projects/:projectId/tasks
❎ GET /orgs/:orgId/teams/:teamId/users/:userId/posts/:postId/comments
```
**Why?**
- Deep nesting makes URLs hard to maintain.

#### b) Flatten with query parameters for complex relationships
```http
✅ GET /tasks?userId=123&projectId=456
```
**Why?**
- Keeps URLs shorter and more readable.
- Avoids deeply nested paths that are difficult to manage.

### 8. Media Types & File Extensions

#### a) Use `Accept` headers for content negotiation
```http
Accept: application/json
Accept: image/png
```
**Why?**
- Allows clients to request different formats.
- More flexible than including format in the URL.

#### b) File extensions for direct resource access
```http
✅ GET /images/logo.jpg
✅ GET /reports/sales.pdf
```
**Why?**
- Makes file type explicit when necessary.
- Useful for directly accessing static content.

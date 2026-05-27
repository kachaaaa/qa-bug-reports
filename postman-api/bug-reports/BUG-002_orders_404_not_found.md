BUG-002: Error 404 Resource not found when creating an order via POST /orders

General Information
* **Project:** Practice Software Testing API
* **Component:** Backend / API / Orders
* **Environment:** REST API / Postman
* **Severity:** Major  (Critical business logic is broken)
* **Priority:** High 

Description / Summary
The backend returns a `404 Resource not found` error when attempting to place an order (`POST /orders`) with a valid, filled cart using the admin Bearer token

Preconditions
* The presence of a valid Bearer administrator token in the Headers

Steps to Reproduce
1. Send a **POST** request to create a new cart: `https://api.practicesoftwaretesting.com/carts` 
  * Request body: empty `{}`
  * Headers: Add `Authorization: Bearer <token>`
  * *Result:* The `cart_id` was received (e.g. `01ksf8ht7ct1f5q3y1prvcqczm`).
2. Send a POST request to add an existing item to the created cart: https://api.practicesoftwaretesting.com/carts/01ksf8ht7ct1f5q3y1prvcqczm
  * Headers: Content-Type: application/json, Authorization: Bearer <token>
  * Request body (JSON):
```json
     {
       "product_id": "01KSF5T55Q79PQ3K2M74SJX52G",
       "quantity": 1
     }
     ```
   * *Result:* Successful response `{"result": "item added or updated"}`.
3. Send a POST request to place an order: `https://api.practicesoftwaretesting.com/orders`
* Headers: `Content-Type: application/json`, `Authorization: Bearer <token>`
* Request body (JSON):
```json
{ 
"cart_id": "01ksf8ht7ct1f5q3y1prvcqczm", 
"payment_method": "Credit Card" 
}
```

Actual Result :
The server returns the status code `404 Not Found`.
*Response body (JSON):*
```json
{
    "message": "Resource not found"
}

Expected Result :
The server returns the 201 Created status code and the created order object, since the passed cart_id exists in the database and contains the product.

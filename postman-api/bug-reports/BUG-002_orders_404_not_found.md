# BUG-002: Error 404 Resource not found when creating an order via POST /orders

## General Information
* **Project:** Practice Software Testing API
* **Component:** Backend / API / Orders
* **Environment:** REST API / Version 12.12.2 (Postman)
* **Severity:** Major (Critical business logic is broken)
* **Priority:** High

## Description / Summary
The backend returns a `404 Resource not found` error when attempting to place an order (`POST /orders`) using a valid, non-empty cart ID, even though a valid administrator Bearer token is provided in the headers.

## Preconditions
* A valid Administrator Bearer token is generated and ready to use.

## Steps to Reproduce
1. **Create a new cart:**
   * Send a `POST` request to: `https://api.practicesoftwaretesting.com/carts`
   * **Headers:** `Authorization: Bearer <admin_token>`
   * **Request Body:** Empty `{}`
   * *Result:* Save the generated `cart_id` from the response (e.g., `01ksf8ht7ct1f5q3y1prvcqczm`).

2. **Add an item to the created cart:**
   * Send a `POST` request to: `https://api.practicesoftwaretesting.com/carts/01ksf8ht7ct1f5q3y1prvcqczm`
   * **Headers:** * `Content-Type: application/json`
     * `Authorization: Bearer <admin_token>`
   * **Request Body (JSON):**
     ```json
     {
       "product_id": "01KSF5T55Q79PQ3K2M74SJX52G",
       "quantity": 1
     }
     ```
   * *Result:* Verify the successful response: `{"result": "item added or updated"}`.

3. **Attempt to submit the order:**
   * Send a `POST` request to: `https://api.practicesoftwaretesting.com/orders`
   * **Headers:** * `Content-Type: application/json`
     * `Authorization: Bearer <admin_token>`
   * **Request Body (JSON):**
     ```json
     { 
       "cart_id": "01ksf8ht7ct1f5q3y1prvcqczm", 
       "payment_method": "Credit Card" 
     }
     ```

## Actual Result
The server blocks the order creation process and returns status code `404 Not Found`.  
**Response Body (JSON):**
```json
{
    "message": "Resource not found"
}

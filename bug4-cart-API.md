Summary : 
The /POST/orders API returns a 404 Resource not found error when attempting to place an order with a valid, full cart using the administrator's Bearer token.

Component : 
Backend / API / Orders 

Severity : 
Major ( Critical business logic is broken, but there is a workaround through the frontend ) 

Priority :
High

Preconditions :
There is a valid administrator Bearer Token

Steps to Reproduce : 

1.Send a POST request to create a new cart: https://api.practicesoftwaretesting.com/carts with an empty body {} and adding the Bearer Token to the headers
- Result: Cart ID received (e.g. 01ksf8ht7ct1f5q3y1prvcqczm)

2.Send a POST request to add an existing product to the created cart: https://api.practicesoftwaretesting.com/carts/01ksf8ht7ct1f5q3y1prvcqczm
- Body (JSON): {"product_id": "01KSF5T55Q79PQ3K2M74SJX52G", "quantity": 1}
- Headers: Content-Type: application/json, Bearer Token attached
- Result: Successful response {"result": "item added or updated"}

3.Send a POST request to place an order:
- https://api.practicesoftwaretesting.com/orders
- Headers: Content-Type: application/json, Bearer Token attached
- Body (JSON):
- {
  "cart_id": "01ksf8ht7ct1f5q3y1prvcqczm",
  "payment_method": "Credit Card"
  }

  Actual Result :
  The server returns a 404 Not Found status with the response body:
  {
    "message": "Resource not found"
}    

  Expected Result :
  The server returns the 201 Created status and the created order object, since the passed        cart_id exists in the database and contains the product

  Environment :
  Practice Software Testing API (Sandbox), Postman

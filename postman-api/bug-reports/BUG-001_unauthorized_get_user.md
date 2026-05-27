BUG-001: Error 401 Unauthorized when retrieving new user data

General Information
* **Project:** Practice Software Testing API
* **Component:** Users / Authentication
* **Environment:** REST API / Postman v10+
* **Severity:** High 
* **Priority:** High 

Description / Summary
The backend returns a `401 Unauthorized` error when sending a public `GET /users/{id}` request immediately after a user has successfully registered, even though no authorization token is issued during the registration process

Steps to Reproduce
1. Open Postman and send a **POST** request to create a user: 
   `https://api.practicesoftwaretesting.com/users/register`
   * Request body (JSON):*
```json
   {
     "first_name": "Tony",
     "last_name": "Stark",
     "phone": "1234567890",
     "dob": "1970-05-29",
     "password": "TonyStark_M4_2026_!!#",
     "email": "stark_iron_boss_2026@stark.com", 
     "address": {
       "street": "Malibu Point",
       "house_number": "10800",
       "city": "Los Angeles",
       "state": "California",
       "country": "USA",
       "postal_code": "90265"
     }
   }
2. Make sure the server returned status 201 Created and copy the generated user id (from the server response)
3. Create a new GET request in Postman to retrieve data for this ID:
https://api.practicesoftwaretesting.com/users/insert_your_ID_here
4. In the Authorization tab, select the No Auth value (the request is sent without a token)
5. Click the Send button

Actual Result :
The server blocks the request and returns a 401 Unauthorized status code.
Response body (JSON):
{
    "message": "Unauthorized"
}

Expected Result :
The request is successful, and the server returns a 200 OK status code and JSON data for the created user's profile. The method should be accessible without authorization, as the security token is missing from the response during registration (POST /users/register)

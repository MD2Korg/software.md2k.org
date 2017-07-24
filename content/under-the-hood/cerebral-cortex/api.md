+++
title = "Cerebral Cortex::API"
description = ""
keywords = []
+++

# Web API


## Auth Login
Returns a json object containing the server's response for an authentication request

* **URL**

    /auth/login

* **Method:**

    `POST`

* **URL Params**

    **Required:**

    `username=[string]`

    `password_hash=[string]`

* **Data Params**

    None

* **Success Response:**

    * **Code:** 200 <br />
      **Content:**

      ```json
      {
        token : auth_token
      }
      ```

* **Error Response:**

    * **Code:** 401 UNAUTHORIZED <br />
      **Content:** `{ error : "Invalid authentication" }`

    OR

    * **Code:** 422 UNPROCESSABLE ENTRY <br />
      **Content:** `{ error : "Email Invalid" }`


* **Sample Call:**

    ```json
    {
        something here
    }
    ```

* **Notes**

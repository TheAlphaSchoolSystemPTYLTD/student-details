**getMedicalSupplementary**
----
  Returns a structured student medical supplementary details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

* **Version:**

  3

* **Permission:**

  Medical Records > Student Medical > Supplementary Info tab > View

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
    `studcode` [string] - Student Code
    
    `msupp_code` [string] - Medical Supplementary Code

   **Optional:**

   None

   **Conditional:**

   None

* **Success Response:**

    ```javascript
    {
      "msupp_code": "HEA",
      "msupp_desc": "Hearing Test",
      "comm_text": "no",
      "__tassversion": "01.053.3.000",
      "token": {
        "msupp_code": "HEA",
        "timestamp": "{ts '2021-01-21 11:20:09'}",
        "studcode": "0009130"
      }
    }
    ```
 
* **Error Response:**

    `studcode` not supplied
    ```javascript
      "error": "studcode is required."
    ```

    `msupp_code` not supplied
    ```javascript
      "error": "msupp_code is required."
    ```

* **Sample Parameters:**

  ```javascript
    {"studcode":"0009130","msupp_code":"HEA"}
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getMedicalSupplementary&appcode=API10&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMedicalSupplementary">
       <input type="hidden" name="appcode" value="API10">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```

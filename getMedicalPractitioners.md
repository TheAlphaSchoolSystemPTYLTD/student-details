**getMedicalPractitioners**
----
  Returns an array of all structured student medical practitioners details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

* **Version:**

  3

* **Permission:**

  Medical Setup > Student Medical > Practitioners tab > View

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
   `studcode [string]` - Student Code

   **Optional:**

   None

   **Conditional:**

   None

* **Success Response:**

    ```javascript
    { 
       "data":[ 
          { 
             "ptype_code":"003",
             "doct_phone":"(02) 3569 7812 xxxxxxxend",
             "doct_name":"Dr Alexander Sebasti Millhouse",
             "ptype_desc":"Chiropractor",
             "prac_num":2
          },
          { 
             "ptype_code":"002",
             "doct_phone":"",
             "doct_name":"Dr Mary Jane Bellingham",
             "ptype_desc":"Doctor",
             "prac_num":9
          }
       ],
       "token":{ 
          "timestamp":"{ts '2020-02-14 09:49:33'}",
          "studcode":"0009130"
       }
    }
    ```
 
* **Error Response:**

    `studcode` not supplied
    ```javascript
      "error": "studcode is required."
    ```

* **Sample Parameters:**

  ```javascript
    {"studcode":"0009130"}
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getMedicalPractitioners&appcode=API10&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMedicalPractitioners">
       <input type="hidden" name="appcode" value="API10">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```
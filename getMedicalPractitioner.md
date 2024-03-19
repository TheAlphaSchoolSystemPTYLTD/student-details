**getMedicalPractitioner**
----
  Returns a structured student medical practitioner details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

* **Version:**

  3

* **Permission:**

  Medical Records > Student Medical > Practitioners tab > View

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
   `studcode [string]` - Student Code

   `prac_num [num]` - Practitioner Code

   **Optional:**

   None

   **Conditional:**

   None

* **Success Response:**

    ```javascript
    {
      "ptype_code": "002",
      "doct_phone": "3020 7900",
      "doct_name": "Dr Mary Jane Bellingham",
      "ptype_desc": "Doctor",
      "prac_num": 9
      "__tassversion": "01.053.3.000",
      "token": {
        "timestamp": "{ts '2021-01-20 16:21:20'}",
        "studcode": "0009130",
        "prac_num": 9
      }
    }
    ```
 
* **Error Response:**

    `studcode` not supplied
    ```javascript
      "error": "studcode is required."
    ```

    `prac_num` not supplied
    ```javascript
      "error": "prac_num is required."
    ```

* **Sample Parameters:**

  ```javascript
    {"studcode":"0009130","prac_num":"9"}
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

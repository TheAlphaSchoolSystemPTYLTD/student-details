**getMedicalConfNote**
----
  Returns a structured student medical condition details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

* **Version:**

  3

* **Permission:**

  Medical Setup > Student Medical > Confidential Notes tab > View

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
   `studcode [string]` - Student Code

   `note_cat [string]` - Medical Note Category

   `note_date [timestamp yyyy-MM-dd HH:mm:ss.SSS]` - Medical Note Date and Time

   **Optional:**

   None

   **Conditional:**

   None

* **Success Response:**

    ```javascript
    {
      "note_cat": "GEN",
      "note_date": "2018-11-01 12:20:04.0",
      "note_date_time": "2018-11-01 12:20:04.0",
      "ncat_desc": "General",
      "note_num": "",
      "note_text": "Andy Confidential General note",
      "entry_code": "tsloman",
      "entry_date": "2018-11-01 00:00:00.0",
      "attach_id": ""
      "attach_url": "",
      "__tassversion": "01.053.3.000",
      "token": {
        "note_date": "2018-11-01 12:20:04.000",
        "timestamp": "{ts '2021-01-20 11:13:31'}",
        "studcode": "0009130",
        "note_cat": "GEN"
      }
    }
    ```
 
* **Error Response:**

    `studcode` not supplied
    ```javascript
      "error": "studcode is required."
    ```

    `note_cat` not supplied
    ```javascript
      "error": "note_cat is required."
    ```

    `note_date` not supplied
    ```javascript
      "error": "note_date is required."
    ```

* **Sample Parameters:**

  ```javascript
    {"studcode":"0009130","note_cat":"GEN","note_date":"2018-11-01 12:20:04.000"}
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getMedicalConfNote&appcode=API10&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMedicalConfNote">
       <input type="hidden" name="appcode" value="API10">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```
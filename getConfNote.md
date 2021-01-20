**getConfNote**
----
  Returns a structured student medical condition details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

* **Version:**

  3

* **Permission:**

  Student Records > Students > Confidential Notes tab > View

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
   `studcode [string]` - Student Code

   `note_cat [string]` - Medical Note Category

   `note_date [string]` - Medical Note Date

   **Optional:**

   None

   **Conditional:**

   None

* **Success Response:**

    ```javascript
    {
      "data": [
        {
          "note_date": "2020-10-01 14:48:14.0",
          "ncat_desc": "Exchange",
          "note_text": "Exchange with her brother today",
          "entry_code": "jason",
          "entry_date": "2020-10-01 00:00:00.0",
          "attach_url": "",
          "attach_id": "",
          "note_cat": "EXC"
        }
      ],
        "__tassversion": "01.053.3.000",
        "token": {
        "note_date": "2019-05-30 15:11:58.0",
        "timestamp": "{ts '2021-01-19 16:30:34'}",
        "studcode": "0009130",
        "note_cat": "APE"
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
    {"studcode":"0009130","note_cat":"APE","note_date":"2019-05-30 15:11:58.0"}
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getConfNote&appcode=API10&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getConfNote">
       <input type="hidden" name="appcode" value="API10">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```
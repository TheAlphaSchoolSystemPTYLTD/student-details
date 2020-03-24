**getNotes**
----
  Returns an array of all structured student medical notes details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

* **Version:**

  3

* **Permission:**

  Student Records > Students > Students > View

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
             "note_date":"2019-09-26 11:06:52.0",
             "ncat_desc":"General",
             "note_text":"Testing with atttachment",
             "entry_code":"fang",
             "entry_date":"2019-09-26 00:00:00.0",
             "attach_url":"inline-file.cfm?do=ui.web.note.attachment&note_cat=GEN&note_date=2019-09-26 11:06:52.0&note_num=&entity_type=S&entity_code=0009130&notetype=standard",
             "attach_id":"2F8F9A77-E2B9-28D5-611EDE1D0A66D623",
             "note_cat":"GEN"
          },
          { 
             "note_date":"2018-09-04 11:05:50.0",
             "ncat_desc":"General",
             "note_text":"Test note only",
             "entry_code":"tsloman",
             "entry_date":"2018-09-04 00:00:00.0",
             "attach_url":"",
             "attach_id":"",
             "note_cat":"GEN"
          }
       ],
       "token":{ 
          "timestamp":"{ts '2020-02-14 15:05:56'}",
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
    http://api.tasscloud.com.au/tassweb/api/?method=getNotes&appcode=API10&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getNotes">
       <input type="hidden" name="appcode" value="API10">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```
**getConfNoteAttachment**
----
  Returns a structured student medical condition attachment details data in JSON format.
  
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

   `attach_id [string]` - Attachment Id

   **Optional:**

   None

   **Conditional:**

   None

* **Success Response:**

    ```javascript
    { 
       "file_size":2217,
       "has_attachment":true,
       "file":"[Base64 encoded image string]",
       "file_name":"recipients.pdf",
       "__tassversion": "01.053.3.000",
       "token":{ 
          "note_date":"2019-09-26 11:06:52.0",
          "timestamp":"{ts '2020-02-14 15:08:55'}",
          "studcode":"0009130",
          "note_cat":"GEN",
          "attach_id":"2F8F9A77-E2B9-28D5-611EDE1D0A66D623"
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

    `attach_id` not supplied
    ```javascript
      "error": "attach_id is required."
    ```

* **Sample Parameters:**

  ```javascript
    {"studcode":"0009130","note_date":"2019-09-26 11:06:52.0","note_cat":"GEN","attach_id":"2F8F9A77-E2B9-28D5-611EDE1D0A66D623"}
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getConfNoteAttachment&appcode=API10&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getConfNoteAttachment">
       <input type="hidden" name="appcode" value="API10">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```
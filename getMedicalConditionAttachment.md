**getMedicalConditionAttachment**
----
  Returns a structured student medical condition attachment details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

* **Version:**

  3

* **Permission:**

  Medical Setup > Student Medical > Medical Conditions tab > View

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
   `studcode [string]` - Student Code

   `mcond_code [string]` - Medical Condition Code

   `attach_id [string]` - Attachment Id

   **Optional:**

   None

   **Conditional:**

   None

* **Success Response:**

    ```javascript
    { 
       "file_size":73771,
       "has_attachment":true,
       "file":"[Base64 encoded image string]",
       "file_name":"testing.JPG",
       "token":{ 
          "timestamp":"{ts '2020-02-14 09:13:41'}",
          "studcode":"0009130",
          "mcond_code":"AST",
          "attach_id":"5F724726-E361-C720-A1160233A4E8893D"
       }
    }
    ```
 
* **Error Response:**

    `studcode` not supplied
    ```javascript
      "error": "studcode is required."
    ```

    `mcond_code` not supplied
    ```javascript
      "error": "mcond_code is required."
    ```

    `attach_id` not supplied
    ```javascript
      "error": "attach_id is required."
    ```

* **Sample Parameters:**

  ```javascript
    {"studcode":"0009130","mcond_code":"AST","attach_id":"5F724726-E361-C720-A1160233A4E8893D"}
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getMedicalConditionAttachment&appcode=API10&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMedicalConditionAttachment">
       <input type="hidden" name="appcode" value="API10">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```
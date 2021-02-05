**getMedicalNotes**
----
  Returns an array of all structured student medical notes details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

  TASS v53.3 PR TBD - Add a new conditional field `currentstatus`, change the required field `studcode` to a conditional field. Add validation for `studcode` and `currentstatus`.

* **Version:**

  3

* **Permission:**

  Medical Setup > Medical Records > Student Medical > Notes tab > View

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
   None

   **Optional:**

   None

   **Conditional:**

   `currentstatus [string]` - Required if `studcode` is not supplied. Must be 'current' or 'future' or 'past' or 'noncurrent'.
 
   `studcode [string]` - Required if `currentstatus` is not supplied. Contains Only One Student Code if supplied.

* **Success Response:**

    when only `studcode` is supplied
    ```javascript
    {
      "data": [
        {
          "note_date": "2018-11-01 12:19:44.0",
          "ncat_desc": "General",
          "note_text": "Andy Standard Medical General Note",
          "entry_code": "tsloman",
          "entry_date": "2018-11-01 00:00:00.0",
          "attach_url": "",
          "attach_id": "",
          "note_cat": "GEN"
        },
        {
          "note_date": "2017-12-08 10:31:23.0",
          "ncat_desc": "General",
          "note_text": "Test 08/12/17",
          "entry_code": "tsloman",
          "entry_date": "2017-12-08 00:00:00.0",
          "attach_url": "",
          "attach_id": "",
          "note_cat": "GEN"
        },
        {
          "note_date": "2016-11-04 11:39:23.0",
          "ncat_desc": "Doctor Advice",
          "note_text": "test, now has an attachment",
          "entry_code": "ale",
          "entry_date": "2016-11-04 00:00:00.0",
          "attach_url": "inline-file.cfm?do=ui.web.note.attachment&entity_code=0009130&entity_type=M&note_cat=DOC&note_date=2016-11-04 11:39:23.0&notetype=standard",
          "attach_id": "E1F63EBE-987B-103A-921C45787AF90D6A",
          "note_cat": "DOC"
        }
      ],
      "__tassversion": "01.053.3.000",
      "token": {
        "timestamp": "{ts '2021-01-20 16:05:15'}",
        "studcode": "0009130"
      }
    }
    ```

    when only `currentstatus` is supplied
    ```javascript
      {
        "data": [
          {
            "mednotes": [
              {
                "note_date": "2016-11-04 00:00:00.0",
                "ncat_desc": "Doctor Advice",
                "note_text": "test",
                "entry_code": "ale",
                "entry_date": "2016-11-04 00:00:00.0",
                "attach_url": "",
                "attach_id": "",
                "note_cat": "DOC"
              },
              {
                "note_date": "2016-11-04 00:00:00.0",
                "ncat_desc": "Dim Whit Note",
                "note_text": "testing 04/11",
                "entry_code": "ale",
                "entry_date": "2016-11-04 00:00:00.0",
                "attach_url": "",
                "attach_id": "",
                "note_cat": "DIM"
              }
            ],
            "studcode": "0009129"
          },
          {
            "mednotes": [
              {
                "note_date": "2018-11-01 12:19:44.0",
                "ncat_desc": "General",
                "note_text": "Andy Standard Medical General Note",
                "entry_code": "tsloman",
                "entry_date": "2018-11-01 00:00:00.0",
                "attach_url": "",
                "attach_id": "",
                "note_cat": "GEN"
              },
              {
                "note_date": "2017-12-08 10:31:23.0",
                "ncat_desc": "General",
                "note_text": "Test 08/12/17",
                "entry_code": "tsloman",
                "entry_date": "2017-12-08 00:00:00.0",
                "attach_url": "",
                "attach_id": "",
                "note_cat": "GEN"
              }
            ],
            "studcode": "0009130"
          }
        ],
        "__tassversion": "01.053.3.000",
        "token": {
          "timestamp": "{ts '2021-01-20 16:07:29'}",
          "currentstatus": "current"
        }
      }
    ```
 
* **Error Response:**

    `studcode` and `currentstatus` are both not supplied
    ```javascript
      "error": "studcode or currentstatus is required."
    ```

    `studcode` contains more than one student code
    ```javascript
      "error": "Only one studcode can be processed at a time."
    ```

    `studcode` does not exist in `currentstatus` student list
    ```javascript
      "error": "[studcode] is not a valid [currentstatus] student."
    ```

    `currentstatus` does not match 'current' or 'future' or 'past' or 'noncurrent'
    ```javascript
      "error": "[currentstatus] must be 'current' or 'future' or 'past' or 'noncurrent'."
    ```
* **Sample Parameters:**

    when `currentstatus` is supplied
  ```javascript
    {"currentstatus":"current"}
  ```

    when `studcode` is supplied
  ```javascript
    {"studcode":"0009130"}
  ```
  
* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getMedicalNotes&appcode=API10&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMedicalNotes">
       <input type="hidden" name="appcode" value="API10">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```
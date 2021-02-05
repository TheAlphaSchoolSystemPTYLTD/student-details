**getConfNotes**
----
  Returns an array of all structured student medical notes details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

  TASS v53.3 PR TBD - Add a new conditional field `currentstatus`, change the required field `studcode` to a conditional field. Add validation for `studcode` and `currentstatus`.

* **Version:**

  3

* **Permission:**

  Student Records > Students > Confidential Notes tab > View

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
      "data":[
        {
          "note_date": "2020-10-01 14:48:14.0",
          "ncat_desc": "Exchange",
          "note_text": "Exchange with her brother today",
          "entry_code": "jason",
          "entry_date": "2020-10-01 00:00:00.0",
          "attach_url": "",
          "attach_id": "",
          "note_cat": "EXC"
        }, 
        { 
          "note_date":"2019-09-26 11:06:52.0",
          "ncat_desc":"General",
          "note_text":"Testing with atttachment",
          "entry_code":"fang",
          "entry_date":"2019-09-26 00:00:00.0",
          "attach_url":"inline-file.cfm?do=ui.web.note.attachment&note_cat=GEN&note_date=2019-09-26 11:06:52.0&note_num=&entity_type=S&entity_code=0009130&notetype=standard",
          "attach_id":"2F8F9A77-E2B9-28D5-611EDE1D0A66D623",
          "note_cat":"GEN"
        }
      ], 
      "__tassversion": "01.053.3.000",
      "token": {
        "timestamp": "{ts '2021-01-19 17:08:36'}",
        "studcode": "0009130"
      }
    }
    ```

    when only `currentstatus` is supplied
    ```javascript
    {
      "data": [
        {
          "studcode": "0009112",
          "studnotes": [
            {
              "note_date": "2012-11-06 00:00:00.0",
              "ncat_desc": "Discipline",
              "note_text": "Test",
              "entry_code": "peterr",
              "entry_date": "2012-11-06 00:00:00.0",
              "attach_url": "",
              "attach_id": "",
              "note_cat": "DIS"
            }
          ]
        },
        {
          "studcode": "0009129",
          "studnotes": [
            {
              "note_date": "2012-11-06 00:00:00.0",
              "ncat_desc": "Discipline",
              "note_text": "Test",
              "entry_code": "peterr",
              "entry_date": "2012-11-06 00:00:00.0",
              "attach_url": "",
              "attach_id": "",
              "note_cat": "DIS"
            }
          ]
        }
      ],
      "__tassversion": "01.053.3.000",
      "token": {
        "timestamp": "{ts '2021-01-20 15:57:38'}",
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
    http://api.tasscloud.com.au/tassweb/api/?method=getConfNotes&appcode=API12&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getConfNotes">
       <input type="hidden" name="appcode" value="API12">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```
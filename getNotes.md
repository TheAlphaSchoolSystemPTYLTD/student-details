**getNotes**
----
  Returns an array of all structured student medical notes details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

  TASS v53.3 PR TBD - Add a new conditional field `currentstatus`, change the required field `studcode` to a conditional field. Add validation for `studcode` and `currentstatus`.

* **Version:**

  3

* **Permission:**

  Student Records > Students > Students > View

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
       "__tassversion": "01.053.3.000",
       "token":{ 
          "timestamp":"{ts '2021-01-21 11:40:11'}",
          "studcode":"0009130"
       }
    }
    ```

    when only `currentstatus` is supplied
    ```javascript
    {
      "data": [
        {
          "studcode": "0009097",
          "studnotes": [
            {
              "note_date": "2015-09-22 00:00:00.0",
              "ncat_desc": "Discipline",
              "note_text": "Eric has been suspended pending a police investigation into and attack over the weekend.",
              "entry_code": "telerik",
              "entry_date": "2015-09-22 00:00:00.0",
              "attach_url": "",
              "attach_id": "",
              "note_cat": "DIS"
            },
            {
              "note_date": "2006-01-11 00:00:00.0",
              "ncat_desc": "Exchange",
              "note_text": "This is certificate.",
              "entry_code": "root",
              "entry_date": "2006-01-11 00:00:00.0",
              "attach_url": "inline-file.cfm?do=ui.web.note.attachment&note_cat=EXC&note_date=2006-01-11 00:00:00.0&note_num=&entity_type=S&entity_code=0009097&notetype=standard",
              "attach_id": "B8432281-0E35-8601-B8EB514137C80C5D",
              "note_cat": "EXC"
            }
          ]
        },
        {
          "studcode": "0009112",
          "studnotes": [
            {
              "note_date": "2005-10-28 00:00:00.0",
              "ncat_desc": "Parental Advice",
              "note_text": "Mrs Boyle sent this in.",
              "entry_code": "ken",
              "entry_date": "2005-10-28 00:00:00.0",
              "attach_url": "inline-file.cfm?do=ui.web.note.attachment&note_cat=PAR&note_date=2005-10-28 00:00:00.0&note_num=&entity_type=S&entity_code=0009112&notetype=standard",
              "attach_id": "35E42E0F-EBA2-CE0A-08AC9F376CEFA3F6",
              "note_cat": "PAR"
            }
          ]
        }
      ],
      "__tassversion": "01.053.3.000",
      "token": {
        "timestamp": "{ts '2021-01-21 11:41:25'}",
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
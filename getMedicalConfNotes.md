**getMedicalConfNotes**
----
  Returns an array of all structured student medical confidential notes details data in JSON format.
  
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

   **Optional:**

   None

   **Conditional:**

   None

* **Success Response:**

    ```javascript
    { 
       "data":[ 
          { 
             "note_date":"2020-01-29 15:33:12.0",
             "ncat_desc":"General",
             "note_text":"Testing CNOTE",
             "entry_code":"fang",
             "entry_date":"2020-01-29 00:00:00.0",
             "attach_url":"inline-file.cfm?do=ui.web.note.attachment&entity_code=0009130&entity_type=M&note_cat=GEN&note_date=2020-01-29 15:33:12.0&notetype=confidential",
             "attach_id":"5DEAB58E-EE13-4565-DC8311946B667C6E",
             "note_cat":"GEN"
          },
          { 
             "note_date":"2015-09-23 00:00:00.0",
             "ncat_desc":"Doctor Advice",
             "note_text":"Dont",
             "entry_code":"telerik",
             "entry_date":"2015-09-23 00:00:00.0",
             "attach_url":"inline-file.cfm?do=ui.web.note.attachment&entity_code=0009130&entity_type=M&note_cat=DOC&note_date=2015-09-23 00:00:00.0&notetype=confidential",
             "attach_id":"B411832E-C017-F1C8-35918C4323EF0297",
             "note_cat":"DOC"
          },
          { 
             "note_date":"2014-09-12 00:00:00.0",
             "ncat_desc":"Parental Advice",
             "note_text":"She has parents.",
             "entry_code":"davidh",
             "entry_date":"2014-09-12 00:00:00.0",
             "attach_url":"",
             "attach_id":"",
             "note_cat":"PAR"
          },
          { 
             "note_date":"2014-09-12 00:00:00.0",
             "ncat_desc":"Nursing Advice",
             "note_text":"Wear a clown mask to scare Andrea.  It's hilarious.",
             "entry_code":"davidh",
             "entry_date":"2014-09-12 00:00:00.0",
             "attach_url":"",
             "attach_id":"",
             "note_cat":"NUR"
          }
       ],
       "token":{ 
          "timestamp":"{ts '2020-02-14 11:14:12'}",
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
    http://api.tasscloud.com.au/tassweb/api/?method=getMedicalConfNotes&appcode=API10&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMedicalConfNotes">
       <input type="hidden" name="appcode" value="API10">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```
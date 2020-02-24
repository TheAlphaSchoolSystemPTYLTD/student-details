**getMedicalNotes**
----
  Returns an array of all structured student medical notes details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

* **Version:**

  3

* **Permission:**

  Medical Setup > Medical Records > Student Medical > Notes tab > View

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
             "note_date":"2019-05-30 15:11:58.0",
             "ncat_desc":"Appendix",
             "note_text":"New note for andy.....",
             "entry_code":"fang",
             "entry_date":"2019-05-30 00:00:00.0",
             "attach_url":"inline-file.cfm?do=ui.web.note.attachment&entity_code=0009130&entity_type=M&note_cat=APE&note_date=2019-05-30 15:11:58.0&notetype=standard",
             "attach_id":"5D2779F0-C855-6569-A3268FF20A391ED0",
             "note_cat":"APE"
          },
          { 
             "note_date":"2018-11-01 12:19:44.0",
             "ncat_desc":"General",
             "note_text":"Andy Standard Medical General Note",
             "entry_code":"tsloman",
             "entry_date":"2018-11-01 00:00:00.0",
             "attach_url":"",
             "attach_id":"",
             "note_cat":"GEN"
          },
          { 
             "note_date":"2016-11-04 11:39:23.0",
             "ncat_desc":"Doctor Advice",
             "note_text":"test, now has an attachment",
             "entry_code":"ale",
             "entry_date":"2016-11-04 00:00:00.0",
             "attach_url":"inline-file.cfm?do=ui.web.note.attachment&entity_code=0009130&entity_type=M&note_cat=DOC&note_date=2016-11-04 11:39:23.0&notetype=standard",
             "attach_id":"E1F63EBE-987B-103A-921C45787AF90D6A",
             "note_cat":"DOC"
          },
          { 
             "note_date":"2015-09-11 00:00:00.0",
             "ncat_desc":"Parental Advice",
             "note_text":"j test",
             "entry_code":"gareth",
             "entry_date":"2015-09-11 00:00:00.0",
             "attach_url":"inline-file.cfm?do=ui.web.note.attachment&entity_code=0009130&entity_type=M&note_cat=PAR&note_date=2015-09-11 00:00:00.0&notetype=standard",
             "attach_id":"430928EB-FBEC-9968-DAE4F938310140ED",
             "note_cat":"PAR"
          }
       ],
       "token":{ 
          "timestamp":"{ts '2020-02-14 10:32:04'}",
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
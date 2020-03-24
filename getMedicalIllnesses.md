**getMedicalIllnesses**
----
  Returns an array of all structured student medical illnesses details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

* **Version:**

  3

* **Permission:**

  Medical Setup > Student Medical > Student Illness/Daily Log > View

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
             "ill_time":"1900-01-01 08:49:00.0",
             "medication_text":"",
             "host_flg":"N",
             "mcond_desc":"Accident",
             "disch_date":"",
             "mcond_code": "ACC",
             "ill_date":"2019-04-12 00:00:00.0",
             "treat_code":"ICE",
             "disch_time":""
          },
          { 
             "ill_time":"1900-01-01 08:49:00.0",
             "medication_text":"",
             "host_flg":"N",
             "mcond_desc":"Mood Disorder",
             "disch_date":"",
             "mcond_code": "MOO",
             "ill_date":"2019-04-08 00:00:00.0",
             "treat_code":"ICE",
             "disch_time":""
          },
          { 
             "ill_time":"1900-01-01 13:21:00.0",
             "medication_text":"",
             "host_flg":"N",
             "mcond_desc":"Asthma",
             "disch_date":"",
             "mcond_code": "AST",
             "ill_date":"2018-12-06 00:00:00.0",
             "treat_code":"VEN",
             "disch_time":""
          }
       ],
       "token":{ 
          "timestamp":"{ts '2020-02-14 10:02:52'}",
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
    http://api.tasscloud.com.au/tassweb/api/?method=getMedicalIllnesses&appcode=API10&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMedicalIllnesses">
       <input type="hidden" name="appcode" value="API10">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```
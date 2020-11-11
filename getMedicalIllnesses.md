**getMedicalIllnesses**
----
  Returns an array of all structured student medical illnesses details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

  TASS v53.3 PR TBD - Add a new conditional field `currentstatus`, change the required field `studcode` to a conditional field. Add validation for `studcode` and `currentstatus`.

* **Version:**

  3

* **Permission:**

  Medical Setup > Student Medical > Student Illness/Daily Log > View

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

    when `currentstatus` is supplied
    ```javascript
    {
      "data":[
        {
          "studcode":"0009130",
          "illness":[
            {
              "ill_time":"1900-01-01 08:49:00.0",
              "medication_text":"",
              "host_flg":"N",
              "mcond_desc":"Accident",
              "disch_date":"",
              "mcond_code":"ACC",
              "ill_date":"2019-04-12 00:00:00.0",
              "treat_code":"ICE",
              "disch_time":""
            },
            {
              "ill_time":"1900-01-01 08:49:00.0",
              "medication_text":"",
              "host_flg":"N",
              "mcond_desc":"Accident",
              "disch_date":"",
              "mcond_code":"ACC",
              "ill_date":"2019-04-11 00:00:00.0",
              "treat_code":"ICE",
              "disch_time":""
            }
          ]
        },
        {
          "studcode":"0009130",
          "illness":[
            {
              "ill_time":"1900-01-01 08:49:00.0",
              "medication_text":"",
              "host_flg":"N",
              "mcond_desc":"Accident",
              "disch_date":"",
              "mcond_code":"ACC",
              "ill_date":"2019-04-12 00:00:00.0",
              "treat_code":"ICE",
              "disch_time":""
            },
            {
              "ill_time":"1900-01-01 08:49:00.0",
              "medication_text":"",
              "host_flg":"N",
              "mcond_desc":"Accident",
              "disch_date":"",
              "mcond_code":"ACC",
              "ill_date":"2019-04-11 00:00:00.0",
              "treat_code":"ICE",
              "disch_time":""
            }
          ]
        }
      ],
      "__tassversion":"01.000.043.0",
      "token":{
        "timestamp":"{ts '2020-11-10 14:24:06'}",
        "studcode":"0009130",
        "currentstatus":"current"
      }
    }
    ```

    when only `studcode` is supplied
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
    {
      "studcode":"0009130",
      "currentstatus":"current"
    }
  ```

    when only `studcode` is supplied
  ```javascript
    {
      "studcode":"0009130"
    }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getMedicalIllnesses&appcode=API12&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMedicalIllnesses">
       <input type="hidden" name="appcode" value="API12">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```
**getMedicalImmunisations**
----
  Returns an array of all structured student medical immunisations details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

  TASS v53.3 PR TBD - Add a new conditional field `currentstatus`, change the required field `studcode` to a conditional field. Add new validations for `studcode` and `currentstatus`.

* **Version:**

  3

* **Permission:**

  Medical Setup > Student Medical > Immunisations tab > View

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
          "immunisations":[
            {
              "imm_desc":"Typhoid",
              "imm_code":"TY",
              "imm_year":2018
            },
            {
              "imm_desc":"Measles",
              "imm_code":"MS",
              "imm_year":2013
            },
            {
              "imm_desc":"Cholera",
              "imm_code":"CH",
              "imm_year":2012
            },
            {
              "imm_desc":"Ros River Fever",
              "imm_code":"RR",
              "imm_year":2011
            }
          ],
          "studcode":"0009130"
        },
        {
          "immunisations":[
            {
              "imm_desc":"Malaria",
              "imm_code":"MA",
              "imm_year":2009
            },
            {
              "imm_desc":"Tetanus",
              "imm_code":"TE",
              "imm_year":2009
            },
            {
              "imm_desc":"Typhoid",
              "imm_code":"TY",
              "imm_year":2009
            }
          ],
          "studcode":"0009096"
        }
      ],
      "__tassversion":"01.000.043.0",
      "token":{
        "timestamp":"{ts '2020-11-10 15:17:43'}",
        "currentstatus":"current"
      }
    }
    ```

    when only `studcode` is supplied
    ```javascript
    { 
       "data":[ 
          { 
             "imm_desc":"Rhubella",
             "imm_code":"RH",
             "imm_year":"Yes"
          },
          { 
             "imm_desc":"Typhoid",
             "imm_code":"TY",
             "imm_year":2018
          }
       ],
       "token":{ 
          "timestamp":"{ts '2020-02-14 09:39:48'}",
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
    http://api.tasscloud.com.au/tassweb/api/?method=getMedicalImmunisations&appcode=API12&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMedicalImmunisations">
       <input type="hidden" name="appcode" value="API12">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```
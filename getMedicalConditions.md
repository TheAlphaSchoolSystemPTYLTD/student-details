**getMedicalConditions**
----
  Returns an array of all structured student medical conditions details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

  TASS v53.3 PR TBD - Add a new conditional field `currentstatus`, change the required field `studcode` to a conditional field. Add validation for `studcode` and `currentstatus`.

* **Version:**

  3

* **Permission:**

  Medical Setup > Student Medical > Medical Conditions tab > View

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

    when `studcode` is supplied
    ```javascript
    {
      "data": [
        {
          "studcode": "0009130",
          "medconditions": [
            {
              "last_occ_date": "2020-08-08 00:00:00.0",
              "mcond_desc": "Accident",
              "mcond_code": "ACC",
              "severe_ind": "N"
            },
            {
              "last_occ_date": "2020-06-24 00:00:00.0",
              "mcond_desc": "ADD",
              "mcond_code": "ADD",
              "severe_ind": "Y"
            },
            {
              "last_occ_date": "2016-01-31 00:00:00.0",
              "mcond_desc": "Anaphylaxis",
              "mcond_code": "ANA",
              "severe_ind": "Y"
            }
          ]
        }
      ],
      "__tassversion": "01.053.3.000",
      "token": {
        "timestamp": "{ts '2021-01-20 11:03:46'}",
        "studcode": "0009130"
      }
    }
    ```

    when `currentstatus` is supplied
    ```javascript
    {
      "data": [
        {
          "studcode": "0009069",
          "medconditions": [
            {
              "last_occ_date": "",
              "mcond_desc": "Anaphylaxis",
              "mcond_code": "ANA",
              "severe_ind": "N"
            },
            {
              "last_occ_date": "2013-07-02 00:00:00.0",
              "mcond_desc": "Asthma",
              "mcond_code": "AST",
              "severe_ind": "N"
            },
            {
              "last_occ_date": "2012-12-04 00:00:00.0",
              "mcond_desc": "Diabetes",
              "mcond_code": "DIA",
              "severe_ind": "Y"
            }
          ]
        },
        {
          "studcode": "0009097",
          "medconditions": [
            {
              "last_occ_date": "2012-12-05 00:00:00.0",
              "mcond_desc": "Diabetes",
              "mcond_code": "DIA",
              "severe_ind": "N"
            },
            {
              "last_occ_date": "2015-03-25 00:00:00.0",
              "mcond_desc": "Hay Fever",
              "mcond_code": "HAY",
              "severe_ind": "N"
            }
          ]
        }
      ],
      "__tassversion": "01.053.3.000",
      "token": {
      "timestamp": "{ts '2021-01-20 12:45:22'}",
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
    http://api.tasscloud.com.au/tassweb/api/?method=getMedicalConditions&appcode=API10&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMedicalConditions">
       <input type="hidden" name="appcode" value="API10">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```
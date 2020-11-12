**getMedicalPractitioners**
----
  Returns an array of all structured student medical practitioners details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

  TASS v53.3 PR TBD - Add a new conditional field `currentstatus`, change the required field `studcode` to a conditional field. Add validation for `studcode` and `currentstatus`.

* **Version:**

  3

* **Permission:**

  Medical Setup > Student Medical > Practitioners tab > View

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
                "practitioners":[
                    {
                        "ptype_code":"SUR",
                        "doct_phone":"8435889727349068572934867",
                        "doct_name":"Dr U R A Fish",
                        "ptype_desc":"General Surgeon",
                        "prac_num":7
                    },
                    {
                        "ptype_code":"006",
                        "doct_phone":"3569 4569",
                        "doct_name":"Dr Zuess",
                        "ptype_desc":"Psychiatrist",
                        "prac_num":3
                    }
                ],
                "studcode":"0009130"
            },
            {
                "practitioners":[
                    {
                        "ptype_code":"002",
                        "doct_phone":"07 3987 4563",
                        "doct_name":"Dr Zuess J",
                        "ptype_desc":"Doctor",
                        "prac_num":1
                    },
                    {
                        "ptype_code":"002",
                        "doct_phone":"",
                        "doct_name":"Dr Godspeed",
                        "ptype_desc":"Doctor",
                        "prac_num":3
                    }
                ],
                "studcode":"0009134"
            }
        ],
        "__tassversion":"01.000.043.0",
        "token":{
            "timestamp":"{ts '2020-11-11 14:41:13'}",
            "currentstatus":"current"
        }
    }
    ```

    when only `studcode` is supplied
    ```javascript
    {
        "data":[
            {
                "ptype_code":"SUR",
                "doct_phone":"8435889727349068572934867",
                "doct_name":"Dr U R A Fish",
                "ptype_desc":"General Surgeon",
                "prac_num":7
            },
            {
                "ptype_code":"006",
                "doct_phone":"3569 4569",
                "doct_name":"Dr Zuess",
                "ptype_desc":"Psychiatrist",
                "prac_num":3
            }
        ],
        "__tassversion":"01.000.043.0",
        "token":{
            "timestamp":"{ts '2020-11-11 14:37:18'}",
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
    http://api.tasscloud.com.au/tassweb/api/?method=getMedicalPractitioners&appcode=API12&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMedicalPractitioners">
       <input type="hidden" name="appcode" value="API12">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```
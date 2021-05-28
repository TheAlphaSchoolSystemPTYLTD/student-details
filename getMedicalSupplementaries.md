**getMedicalSupplementaries**
----
  Returns an array of all structured student medical supplementaries details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

  TASS v54.0 - Add a new conditional field `currentstatus`, change the required field `studcode` to a conditional field. Add new validations for `studcode` and `currentstatus`.

* **Version:**

  3

* **Permission:**

  Medical Setup > Student Medical > Supplementary Info tab > View

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
                "supplementaries":[
                    {
                        "msupp_code":"DEN",
                        "msupp_desc":"Dental Test",
                        "comm_text":"test"
                    },
                    {
                        "msupp_code":"VIS",
                        "msupp_desc":"Vision Tests",
                        "comm_text":"can see stuff with and without her glasses."
                    }
                ],
                "studcode":"0009130"
            },
            {
                "supplementaries":[
                    {
                        "msupp_code":"HEA",
                        "msupp_desc":"Hearing Test",
                        "comm_text":"Has normal hearing range. J"
                    },
                    {
                        "msupp_code":"VIS",
                        "msupp_desc":"Vision Tests",
                        "comm_text":"Now you can see me"
                    }
                ],
                "studcode":"0009134"
            }
        ],
        "__tassversion":"01.000.043.0",
        "token":{
            "timestamp":"{ts '2020-11-11 15:04:47'}",
            "currentstatus":"current"
        }
    }
    ```

    when only `studcode` is supplied
    ```javascript
    {
        "data":[
            {
                "msupp_code":"DEN",
                "msupp_desc":"Dental Test",
                "comm_text":"test"
            },
            {
                "msupp_code":"VIS",
                "msupp_desc":"Vision Tests",
                "comm_text":"can see stuff with and without her glasses."
            }
        ],
        "__tassversion":"01.000.043.0",
        "token":{
            "timestamp":"{ts '2020-11-11 15:03:01'}",
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
    http://api.tasscloud.com.au/tassweb/api/?method=getMedicalSupplementaries&appcode=API12&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMedicalSupplementaries">
       <input type="hidden" name="appcode" value="API12">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```

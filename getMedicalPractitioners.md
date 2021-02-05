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

    when only `studcode` is supplied
    ```javascript
    {
      "data": [
        {
        "ptype_code": "003",
        "doct_phone": "(02) 3569 7812 xxxxxxxend",
        "doct_name": "Dr Alexander Sebasti Millhouse",
        "ptype_desc": "Chiropractor",
        "prac_num": 2
        },
        {
        "ptype_code": "003",
        "doct_phone": "wqergf",
        "doct_name": "qwerf",
        "ptype_desc": "Chiropractor",
        "prac_num": 16
        }
      ],
      "__tassversion": "01.053.3.000",
      "token": {
      "timestamp": "{ts '2021-01-20 17:24:27'}",
      "studcode": "0009130"
      }
    }
    ```

    when only `currentstatus` is supplied
    ```javascript
    {
      "data": [
        {
          "practitioners": [
            {
              "ptype_code": "003",
              "doct_phone": "07 33550643",
              "doct_name": "Dr George Quinn Phd",
              "ptype_desc": "Chiropractor",
              "prac_num": 1
            },
            {
              "ptype_code": "003",
              "doct_phone": "0423 679 908",
              "doct_name": "Dr G M Quinn",
              "ptype_desc": "Chiropractor",
              "prac_num": 2
            }
          ],
          "studcode": "0009069"
        },
        {
          "practitioners": [
            {
              "ptype_code": "003",
              "doct_phone": "+61 7 3841 1475",
              "doct_name": "Dr Cathy Louise McMillan",
              "ptype_desc": "Chiropractor",
              "prac_num": 2
            },
            {
              "ptype_code": "001",
              "doct_phone": "+61 7 3841 4542",
              "doct_name": "Mr Keith Daniel Farthing",
              "ptype_desc": "Dentist",
              "prac_num": 1
            }
          ],
          "studcode": "0009213"
        }
      ],
      "__tassversion": "01.053.3.000",
      "token": {
        "timestamp": "{ts '2021-01-21 11:04:57'}",
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
    http://api.tasscloud.com.au/tassweb/api/?method=getMedicalPractitioners&appcode=API10&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMedicalPractitioners">
       <input type="hidden" name="appcode" value="API10">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```
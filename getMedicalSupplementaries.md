**getMedicalSupplementaries**
----
  Returns an array of all structured student medical supplementaries details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

  TASS v54.0 - Add a new conditional field `currentstatus`, change the required field `studcode` to a conditional field. Add validation for `studcode` and `currentstatus`.

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

    when only `studcode` is supplied
    ```javascript
    {
      "data": [
        {
          "msupp_code": "DEN",
          "msupp_desc": "Dental Test",
          "comm_text": "test"
        },
        {
          "msupp_code": "FIT",
          "msupp_desc": "Fitness Tests xxxx20",
          "comm_text": "Andy is a lazy little bludger and hence is quite overweight.  She cannot run further than 20 meters and don't even think of asking her to do something drastic like a situp or starjump.  She needs to s"
        },
        {
          "msupp_code": "HEA",
          "msupp_desc": "Hearing Test",
          "comm_text": "no"
        },
        {
          "msupp_code": "VIS",
          "msupp_desc": "Vision Tests",
          "comm_text": "can see stuff with and without her glasses."
        }
      ],
      "__tassversion": "01.053.3.000",
      "token": {
        "timestamp": "{ts '2021-01-21 11:10:39'}",
        "studcode": "0009130"
      }
    }

    ```

    when only `currentstatus` is supplied
    ```javascript
    {
      "data": [
        {
          "supplementaries": [
            {
              "msupp_code": "DEN",
              "msupp_desc": "Dental Test",
              "comm_text": "test"
            },
            {
              "msupp_code": "FIT",
              "msupp_desc": "Fitness Tests xxxx20",
              "comm_text": "Andy is a lazy little bludger and hence is quite overweight.  She cannot run further than 20 meters and don't even think of asking her to do something drastic like a situp or starjump.  She needs to s"
            },
            {
              "msupp_code": "HEA",
              "msupp_desc": "Hearing Test",
              "comm_text": "no"
            },
            {
              "msupp_code": "VIS",
              "msupp_desc": "Vision Tests",
              "comm_text": "can see stuff with and without her glasses."
            }
          ],
          "studcode": "0009130"
        },
        {
          "supplementaries": [
            {
              "msupp_code": "HEA",
              "msupp_desc": "Hearing Test",
              "comm_text": "Excellent hearing"
            }
          ],
          "studcode": "0009213"
        }
      ],
      "__tassversion": "01.053.3.000",
      "token": {
        "timestamp": "{ts '2021-01-21 11:12:38'}",
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
    http://api.tasscloud.com.au/tassweb/api/?method=getMedicalSupplementaries&appcode=API10&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMedicalSupplementaries">
       <input type="hidden" name="appcode" value="API10">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```

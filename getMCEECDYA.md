**getMCEECDYA**
----
  Returns structured MCEECDYA data in JSON format.
  
* **Version History:**

  TASS v53.0 - Method Added

  TASS v53.3 PR TBD - Add a new conditional field `currentstatus`, change the required field `studcode` to a conditional field. Add new validations for `studcode` and `currentstatus`.

* **Version:**

  3

* **Permission:**

  Student Records > Students > MCEECDYA (tab)

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
      "student": {
        "S_INDIG_STS": {
          "code": 1,
          "desc": "Aboriginal"
        },
        "SLOTE_CODE": {
          "code": 3403,
          "desc": "Ukrainian"
        },
        "SCOB_CODE": {
          "code": 6105,
          "desc": "Taiwan"
        },
        "ARRIVE_YR": {
          "code": 2019,
          "desc": "ARRIVE_YR"
        }
      },
      "parent1": {
        "MLOTE_CODE": {
          "code": 6100,
          "desc": "Burman"
        },
        "MSE_CODE": {
          "code": 4,
          "desc": "Year 12 or equivalent"
        },
        "MNSE_CODE": {
          "code": 7,
          "desc": "Bachelor degree or above"
        },
        "MOCC_CODE": {
          "code": 9,
          "desc": 9
        }
      },
      "parent2": {
        "FOCC_CODE": {
          "code": 9,
          "desc": 9
        },
        "FSE_CODE": {
          "code": 2,
          "desc": "Year 10 or equivalent"
        },
        "FLOTE_CODE": {
          "code": 6402,
          "desc": "Thai"
        },
        "FNSE_CODE": {
          "code": 6,
          "desc": "Advanced diploma / Diploma"
        }
      },
      "__tassversion": "01.053.3.000",
      "token": {
        "timestamp": "{ts '2021-01-19 17:16:00'}",
        "studcode": "0009130"
      }
    }
    ```

    when `currentstatus` is supplied
    ```javascript
      {
        "data": [
            {
            "student": {
              "S_INDIG_STS": {
                "code": 9,
                "desc": "Unknown"
              },
              "SLOTE_CODE": {
                "code": "",
                "desc": ""
              },
              "SCOB_CODE": {
                "code": 1101,
                "desc": "Australia"
              },
              "ARRIVE_YR": {
                "code": "",
                "desc": "ARRIVE_YR"
              }
            },
            "parent1": {
              "MLOTE_CODE": {
                "code": "",
                "desc": ""
              },
              "MSE_CODE": {
                "code": "",
                "desc": ""
              },
              "MNSE_CODE": {
                "code": "",
                "desc": ""
              },
              "MOCC_CODE": {
                "code": "",
                "desc": ""
              }
            },
            "parent2": {
              "FOCC_CODE": {
                "code": "",
                "desc": ""
              },
              "FSE_CODE": {
                "code": "",
                "desc": ""
              },
              "FLOTE_CODE": {
                "code": "",
                "desc": ""
              },
              "FNSE_CODE": {
                "code": "",
                "desc": ""
              }
            },
            "studcode": "0009276"
          }
        ],
        "__tassversion": "01.000.043.0",
        "token": {
          "timestamp": "{ts '2021-01-20 11:29:49'}",
          "currentstatus": "current"
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

    `studcode` has no MCEECDYA record
    ```javascript
      {
        "__status": "invalid",
        "__msg": "Student has no MCEECDYA Data.",
        "__invalid": {}
      }
    ```
    
* **Sample Parameters:**

    when `studcode` is supplied
  ```javascript
    {"studcode":"0009130"}
  ```

    when `currentstatus` is supplied
  ```javascript
    {"currentstatus":"current"}
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getMCEECDYA&appcode=API12&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMCEECDYA">
       <input type="hidden" name="appcode" value="API12">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```

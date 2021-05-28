**getMCEECDYA**
----
  Returns structured MCEECDYA data in JSON format.
  
* **Version History:**

  TASS v53.0 - Method Added

  TASS v54.0 - Add a new conditional field `currentstatus`, change the required field `studcode` to a conditional field. Add new validations for `studcode` and `currentstatus`.

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

    when `currentstatus` is supplied
    ```javascript
    {
        "data":[
            {
                "student":{
                    "S_INDIG_STS":{
                        "code":1,
                        "desc":"Aboriginal"
                    },
                    "SLOTE_CODE":{
                        "code":3503,
                        "desc":"Croatian"
                    },
                    "SCOB_CODE":{
                        "code":4215,
                        "desc":"Turkey"
                    },
                    "ARRIVE_YR":{
                        "code":2001,
                        "desc":"ARRIVE_YR"
                    }
                },
                "parent1":{
                    "MLOTE_CODE":{
                        "code":3503,
                        "desc":"Croatian"
                    },
                    "MSE_CODE":{
                        "code":4,
                        "desc":"Year 12 or equivalent"
                    },
                    "MNSE_CODE":{
                        "code":7,
                        "desc":"Bachelor degree or above"
                    },
                    "MOCC_CODE":{
                        "code":3,
                        "desc":3
                    }
                },
                "parent2":{
                    "FOCC_CODE":{
                        "code":2,
                        "desc":2
                    },
                    "FSE_CODE":{
                        "code":2,
                        "desc":"Year 10 or equivalent"
                    },
                    "FLOTE_CODE":{
                        "code":4300,
                        "desc":"Turkish and Central Asian Languages"
                    },
                    "FNSE_CODE":{
                        "code":8,
                        "desc":"No non-school qualification"
                    }
                },
                "studcode":"0009130"
            },
            {
                "student":{
                    
                },
                "parent1":{
                    
                },
                "parent2":{
                    
                },
                "error":"Student has no MCEECDYA Data.",
                "studcode":"0009134"
            }
        ],
        "__tassversion":"01.000.043.0",
        "token":{
            "timestamp":"{ts '2020-11-12 10:52:02'}",
            "currentstatus":"current"
        }
    }
    ```

    when only `studcode` is supplied
    ```javascript
    {
        "student":{
            "S_INDIG_STS":{
                "code":1,
                "desc":"Aboriginal"
            },
            "SLOTE_CODE":{
                "code":3503,
                "desc":"Croatian"
            },
            "SCOB_CODE":{
                "code":4215,
                "desc":"Turkey"
            },
            "ARRIVE_YR":{
                "code":2001,
                "desc":"ARRIVE_YR"
            }
        },
        "__tassversion":"01.000.043.0",
        "parent1":{
            "MLOTE_CODE":{
                "code":3503,
                "desc":"Croatian"
            },
            "MSE_CODE":{
                "code":4,
                "desc":"Year 12 or equivalent"
            },
            "MNSE_CODE":{
                "code":7,
                "desc":"Bachelor degree or above"
            },
            "MOCC_CODE":{
                "code":3,
                "desc":3
            }
        },
        "parent2":{
            "FOCC_CODE":{
                "code":2,
                "desc":2
            },
            "FSE_CODE":{
                "code":2,
                "desc":"Year 10 or equivalent"
            },
            "FLOTE_CODE":{
                "code":4300,
                "desc":"Turkish and Central Asian Languages"
            },
            "FNSE_CODE":{
                "code":8,
                "desc":"No non-school qualification"
            }
        },
        "token":{
            "timestamp":"{ts '2020-11-12 10:38:17'}",
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

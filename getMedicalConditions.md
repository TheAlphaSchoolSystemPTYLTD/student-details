**getMedicalConditions**
----
  Returns an array of all structured student medical conditions details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

  TASS v54.0 - Add a new conditional field `currentstatus`, change the required field `studcode` to a conditional field. Add new validations for `studcode` and `currentstatus`.

  TASS v56.5 - Add a new optional field `includemedication`, new return data `general_note` within `medconditions` array.
               Add a conditional return data `medication_requirements` within `medconditions` array

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

    `includemedication [boolean]` - Must be 'true' or 'false'. If it is not provided, treat it as 'false'.

   **Conditional:**

    `currentstatus [string]` - Required if `studcode` is not supplied. Must be 'current' or 'future' or 'past' or 'noncurrent'.

    `studcode [string]` - Required if `currentstatus` is not supplied. Contains Only One Student Code if supplied.

* **Success Response:**

    when only `studcode` is supplied
    ```javascript
    {
      "data": [
        {
          "last_occ_date": "2018-01-30 00:00:00.0",
          "mcond_desc": "Accident",
          "mcond_code": "ACC",
          "severe_ind": "N"
        },
        {
          "last_occ_date": "2016-01-31 00:00:00.0",
          "mcond_desc": "Anaphylaxis",
          "mcond_code": "ANA",
          "severe_ind": "Y"
        }
      ],
      "token": {
        "timestamp": "{ts '2020-02-13 16:56:20'}",
        "studcode": "0009130"
      }
    }
    ```

    when only `currentstatus` is supplied
    ```javascript
    {
        "data":[
            {
                "studcode":"0009130",
                "medconditions":[
                    {
                        "last_occ_date":"2018-01-30 00:00:00.0",
                        "mcond_desc":"Accident",
                        "mcond_code":"ACC",
                        "severe_ind":"N",
                        "general_note": "Must not have running exercise"
                    },
                    {
                        "last_occ_date":"2016-01-31 00:00:00.0",
                        "mcond_desc":"Anaphylaxis",
                        "mcond_code":"ANA",
                        "severe_ind":"Y",
                        "general_note": "Has suffered Anaphylaxis since birth."
                    }
                ]
            },
            {
                "studcode":"0009134",
                "medconditions":[
                    {
                        "last_occ_date":"",
                        "mcond_desc":"Asthma",
                        "mcond_code":"AST",
                        "severe_ind":"N",
                        "general_note": "Minimise the outdoor activity."
                    }
                ]
            }
        ],
        "__tassversion":"01.000.043.0",
        "token":{
            "timestamp":"{ts '2020-11-11 14:01:03'}",
            "currentstatus":"current"
        }
    }
    ```
    when `currentstatus` is supplied and `includemedication` is supplied as 'true'
    ```javascript
    {
      "data": [
        {
            "studcode":"0009130",
            "medconditions":[
                {
                    "last_occ_date":"2018-01-30 00:00:00.0",
                    "mcond_desc": "Anaphylaxis",
                    "general_note": "Has suffered Anaphylaxis since birth.",
                    "mcond_code": "ANA",
                    "severe_ind": "Y",
                    "medication_requirements": [
                        {
                            "med_detl": "To reduce allergic response",
                            "med_text": "Epinephrine",
                            "med_meth": "Injection"
                        },
                        {
                            "med_detl": "To help you breathe",
                            "med_text": "Oxygen bag",
                            "med_meth": "Bag valve mask"
                        }
                    ]
                }
            ]
        }
      ]
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

    `includemedication` does not match 'true' or 'fasle'
    ```javascript
      "error": "[includemedication] must be 'true' or 'false'."
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

      when `currentstatus` is supplied and `includemedication` is supplied
  ```javascript
    {
      "currentstatus":"current"
      ,"includemedication":"true"
    }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getMedicalConditions&appcode=API12&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMedicalConditions">
       <input type="hidden" name="appcode" value="API12">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```

**getMedicalGeneral**
----
  Returns student general medical details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

  TASS v54.0 - Add a new conditional field `currentstatus`, change the required field `studcode` to a conditional field. Add new validations for `studcode` and `currentstatus`.

* **Version:**

  3

* **Permission:**

  Medical Setup > Student Medical > View

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
                "contacts":[
                    {
                        "contact_name":"Mrs P Clarké Second Line",
                        "medical_townsub":"ALBION",
                        "medical_home_phone":"3870 9987",
                        "medical_addr1":"",
                        "medical_country":"AUSTRALIA",
                        "medical_addr2":"123 Smith Rd",
                        "medical_mob_phone2":"",
                        "medical_addr3":"the bag end of nowhere",
                        "medical_post_code":4005,
                        "medical_bus_phone":"3201 1302",
                        "medical_mob_phone":"0427203657",
                        "medical_state_code":"NT"
                    }
                ],
                "swimingLevel":"Can swim 50m",
                "surname":"Clark",
                "given_name":"Andréa Joan",
                "mud_fields":{
                    "Panadol/Aspirin":"Y",
                    "Allergies2":"YES",
                    "Fifth Text Desc":"",
                    "Allergies":"N",
                    "Diabeties":"Y",
                    "Measles":"N",
                    "Blood Group":"A",
                    "Preferred Hospital":"WE",
                    "Private Health No.":"903600060139933770",
                    "Private Health Insur":"N",
                    "Health Insurance Co":"MP",
                    "Consent Form":"ATH",
                    "ADHD Medication":"RIT"
                },
                "preferred_name":"Andy",
                "studcode":"0009130"
            },
            {
                "contacts":[
                    
                ],
                "swimingLevel":"Can swim 50m",
                "surname":"Clark",
                "given_name":"Lauren Jane",
                "mud_fields":{
                    "Panadol/Aspirin":"N",
                    "Allergies2":"",
                    "Fifth Text Desc":"",
                    "Allergies":"N",
                    "Diabeties":"",
                    "Measles":"Y",
                    "Blood Group":"",
                    "Preferred Hospital":"MA",
                    "Private Health No.":"",
                    "Private Health Insur":"N",
                    "Health Insurance Co":"MP",
                    "Consent Form":"ATH",
                    "ADHD Medication":""
                },
                "preferred_name":"Lauren",
                "studcode":"0009134"
            }
        ],
        "__tassversion":"01.000.043.0",
        "token":{
            "timestamp":"{ts '2020-11-11 13:44:32'}",
            "currentstatus":"current"
        }
    }
    ```

    when only `studcode` is supplied
    ```javascript
    {
        "contacts":[
            {
                "contact_name":"Mrs P Clarké Second Line",
                "medical_townsub":"ALBION",
                "medical_home_phone":"3870 9987",
                "medical_addr1":"",
                "medical_country":"AUSTRALIA",
                "medical_addr2":"123 Smith Rd",
                "medical_mob_phone2":"",
                "medical_addr3":"the bag end of nowhere",
                "medical_post_code":4005,
                "medical_bus_phone":"3201 1302",
                "medical_mob_phone":"0427203657",
                "medical_state_code":"NT"
            }
        ],
        "swimingLevel":"Can swim 50m",
        "surname":"Clark",
        "given_name":"Andréa Joan",
        "mud_fields":{
            "Panadol/Aspirin":"Y",
            "Allergies2":"YES",
            "Fifth Text Desc":"",
            "Allergies":"N",
            "Diabeties":"Y",
            "Measles":"N",
            "Blood Group":"A",
            "Preferred Hospital":"WE",
            "Private Health No.":"903600060139933770",
            "Private Health Insur":"N",
            "Health Insurance Co":"MP",
            "Consent Form":"ATH",
            "ADHD Medication":"RIT"
        },
        "stud_code":"0009130",
        "__tassversion":"01.000.043.0",
        "preferred_name":"Andy",
        "token":{
            "timestamp":"{ts '2020-11-11 13:37:12'}",
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
    http://api.tasscloud.com.au/tassweb/api/?method=getMedicalGeneral&appcode=API12&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMedicalGeneral">
       <input type="hidden" name="appcode" value="API12">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```
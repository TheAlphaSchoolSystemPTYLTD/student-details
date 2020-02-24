**getMedicalGeneral**
----
  Returns student general medical details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

* **Version:**

  3

* **Permission:**

  Medical Setup > Student Medical > View

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
   `studcode [string]` - Student Code

   **Optional:**

   None

   **Conditional:**

   None

* **Success Response:**

    ```javascript
    {
        "contacts": [
            {
                "contact_name": "Mrs P Clarké Second Line",
                "medical_townsub": "ALBION",
                "medical_home_phone": "3870 9987",
                "medical_addr1": "",
                "medical_country": "AUSTRALIA",
                "medical_addr2": "123 Smith Rd",
                "medical_mob_phone2": "",
                "medical_addr3": "the bag end of nowhere",
                "medical_post_code": 4005,
                "medical_bus_phone": "3201 1302",
                "medical_mob_phone": "0427203657",
                "medical_state_code": "NT"
            }
        ],
        "swimingLevel": "Can swim 50m",
        "surname": "Clark",
        "given_name": "Andréa Joan",
        "mud_fields": {
            "Panadol/Aspirin": "Y",
            "Allergies2": "YES",
            "Fifth Text Desc": "",
            "Allergies": "N",
            "Diabeties": "Y",
            "Measles": "N",
            "Blood Group": "A",
            "Preferred Hospital": "WE",
            "Private Health No.": "903600060139933770",
            "Private Health Insur": "N",
            "Health Insurance Co": "MP",
            "Consent Form": "ATH",
            "ADHD Medication": "RIT"
        },
        "stud_code": "0009130",
        "preferred_name": "Andy",
        "token": {
            "timestamp": "{ts '2020-02-13 16:52:24'}",
            "studcode": "0009130"
        }
    }
    ```
 
* **Error Response:**

    `studcode` not supplied
    ```javascript
      "error": "studcode is required."
    ```

* **Sample Parameters:**

  ```javascript
    {"studcode":"0009130"}
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getMedicalGeneral&appcode=API10&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMedicalGeneral">
       <input type="hidden" name="appcode" value="API10">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```
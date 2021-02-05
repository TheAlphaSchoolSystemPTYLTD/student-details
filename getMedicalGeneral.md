**getMedicalGeneral**
----
  Returns student general medical details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

  TASS v53.3 PR TBD - Add a new conditional field `currentstatus`, change the required field `studcode` to a conditional field. Add new validations for `studcode` and `currentstatus`.

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

    when `studcode` is supplied
    ```javascript
    {
      "contacts": [
        {
          "contact_name": "Mrs E Clark and the lesser Clarks for the giant wombock trees",
          "medical_townsub": "TOOWONG",
          "medical_home_phone": "3870 9987",
          "medical_addr1": "Gigi Lodge \"Shelta\"",
          "medical_country": "",
          "medical_addr2": "24 Augustus 'Street'",
          "medical_mob_phone2": "0412016500",
          "medical_addr3": "",
          "medical_post_code": 4066,
          "medical_bus_phone": "3201 1302",
          "medical_mob_phone": "0434542770",
          "medical_state_code": "QLD"
        }
      ],
      "swimingLevel": "Can float with assistance but will sink like a rock if unass",
      "surname": "Clark",
      "given_name": "Andréa Joan",
      "preferred_name": "Andy",
      "stud_code": "0009130",
      "mud_fields": {
        "Panadol/Aspirin": "N",
        "Allergies2": "YES",
        "Allergies": "Y",
        "Diabeties": "",
        "Measles": "N",
        "Blood Group": "A+",
        "Preferred Hospital": "WE",
        "Private Health No.": "703600060139933770",
        "Private Health Insur": "N",
        "Health Insurance Co": "MP",
        "Consent Form": "ATH",
        "ADHD Medication": "RAK"
      },
      "__tassversion": "01.053.3.000",
      "token": {
        "timestamp": "{ts '2021-01-20 13:28:59'}",
        "studcode": "0009130"
      }
    }
    ```

    when `currentstatus` is supplied
    ```javascript
    {
      "data": [
        {
          "contacts": [],
          "swimingLevel": "",
          "surname": "Ratnik9",
          "given_name": "Kirsten7 Delila5",
          "preferred_name": "Kirsten6",
          "studcode": "0021265"
          "mud_fields": {
            "Panadol/Aspirin": "",
            "Allergies2": "",
            "Allergies": "",
            "Diabeties": "",
            "Measles": "",
            "Blood Group": "",
            "Preferred Hospital": "",
            "Private Health No.": "",
            "Private Health Insur": "",
            "Health Insurance Co": "",
            "Consent Form": "",
            "ADHD Medication": ""
          },
        },
        {
          "contacts": [
            {
              "contact_name": "Mrs E Clark and the lesser Clarks for the giant wombock trees",
              "medical_townsub": "TOOWONG",
              "medical_home_phone": "3870 9987",
              "medical_addr1": "Gigi Lodge \"Shelta\"",
              "medical_country": "",
              "medical_addr2": "24 Augustus 'Street'",
              "medical_mob_phone2": "0412016500",
              "medical_addr3": "",
              "medical_post_code": 4066,
              "medical_bus_phone": "3201 1302",
              "medical_mob_phone": "0434542770",
              "medical_state_code": "QLD"
            }
          ],
          "swimingLevel": "Can float with assistance but will sink like a rock if unass",
          "surname": "Clark",
          "given_name": "Andréa Joan",
          "preferred_name": "Andy",
          "stud_code": "0009130",
          "mud_fields": {
            "Panadol/Aspirin": "N",
            "Allergies2": "YES",
            "Allergies": "Y",
            "Diabeties": "",
            "Measles": "N",
            "Blood Group": "A+",
            "Preferred Hospital": "WE",
            "Private Health No.": "703600060139933770",
            "Private Health Insur": "N",
            "Health Insurance Co": "MP",
            "Consent Form": "ATH",
            "ADHD Medication": "RAK"
          }
        }
      ],
      "__tassversion": "01.053.3.000",
      "token": {
      "timestamp": "{ts '2021-01-20 13:34:58'}",
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
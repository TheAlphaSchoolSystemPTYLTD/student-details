**getStudentsDetails**
----
  Returns an array of structured Student data comprising general, school, and other school details in JSON format.

* **Version:**

  2
  
* **Version History:**

  New Property `addressee` added in Version 51.4. Erroneous `adressee` field is depreciated and will be removed in a future version.

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**

   `currentstatus [string]` -  Must be 'current' or 'future' or 'past' or 'noncurrent'
   
   **Optional:**

   `code [string]` - Student code
   
   `includephoto [boolean]` -  Must be 'true' or 'false' for whether returning student photo.

   `thumbnail [boolean]` -  Must be 'true' or 'false' for whether returning student thumbnail photo.

   `campus [string]` -  Campus Code.

   `pc_tutor_group [string]` -  Tutor Group Code.

   `class [string]` -  Student Class.

   `year_group [string]` -  Numeric Year Group Value.

   **Conditional:**
 
   none

* **Success Response:**

    ```javascript
      "students": [
        {
          "general_details": {
            "surname": "Angus",
            "next_year_indicator": "Advancing",
            "date_of_leaving": "",
            "student_code": 20073,
            "usi": "",
            "mobile_phone": "                              ",
            "lui_number": "",
            "entry_year_group": 8,
            "par_code": "002082",
            "sms_flg": "N",
            "religion": "Anglican",
            "preferred_name": "Paul",
            "gender": "Male",
            "date_of_entry": "19/01/1998",
            "student_photo": {
              "file_info": {
                "image": "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",
                "file_name": "tn_20073.jpg",
                "mime_type": "image/jpeg"
              }
            },
            "date_of_birth": "15/10/1994",
            "alternate_id": "098765432",
            "given_names": "Paul"
          },
          "school_details": {
            "campus": "Senior School (Curlew St)",
            "email_address": "angu001@tassweb.com.au",
            "pc_tutor_group": "A1",
            "boarder": "Yes",
            "student_cafe_access": "No",
            "house": "Banksia",
            "year_group": 11,
            "form_class": "A",
            "residency_status": "Overseas Student"
          },
          "other_school_details": {
            "parish": "Chermside",
            "library_card_no.": "",
            "support_teacher_req.": "N",
            "scholarship": "",
            "returning_student": "Y",
            "media_consent": "Y",
            "learning_support": "N",
            "locker_number": "",
            "reason_for_leaving": "",
            "licence_plate": "",
            "external_tuition": "N",
            "international_stud.": "",
            "drivers_licence": "",
            "diet_restrictions": ""
          }
        }
      ]
    ```
 
* **Error Response:**

    `currentstatus` not supplied
    ```javascript
    __invalid: {
      "currentstatus": "field is required"
    }
    ```

    `currentstatus` not be 'current' or 'future' or 'past' or 'noncurrent'
    ```javascript
    __invalid: {
      "currentstatus": "Current Status must be 'current' or 'future' or 'past' or 'noncurrent'."
    }
    ```

    `code` invalid
    ```javascript
    __invalid: {
      "code": "Student Code is invalid."
    }
    ```
    
    `includephoto` not a valid boolean
    ```javascript
    __invalid: {
      "includephoto": "Value is not a valid boolean."
    }
    ```

    `thumbnail` not a valid boolean
    ```javascript
    __invalid: {
      "thumbnail": "Value is not a valid boolean."
    }
    ```

    `campus` not a valid campus code
    ```javascript
    __invalid: {
      "campus": "Invalid campus [campus]."
    }
    ```

    `pc_tutor_group` not a valid tutor group
    ```javascript
    __invalid: {
      "campus": "Invalid pc_tutor_group [pc_tutor_group]."
    }
    ```

    `class` not a valid class
    ```javascript
    __invalid: {
      "campus": "Invalid class [class]."
    }
    ```

    `year_group` not a valid year group
    ```javascript
    __invalid: {
      "campus": "Invalid year_group [year_group]."
    }
    ```
    
* **Sample Parameters:**

  ```javascript
    { 
      "currentstatus":"current",
      "code":"20073",
      "includephoto":"true",
      "thumbnail":"true"
    }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=GetStudentsDetails&appcode=DEMOSD&company=10&v=2&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We1Gqx9%2Fzb%2BcbVFartivsDN%2FxGgAIIjtABAYfzYPqTCpLf3gb0nW3h%2FTrPFLMhAdNcVvHD0Gz4FkRj5jRAD1aAGQ
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getStudentsDetails">
       <input type="hidden" name="appcode" value="DEMOSD">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We1Gqx9/zb+cbVFartivsDN/xGgAIIjtABAYfzYPqTCpLf3gb0nW3h/TrPFLMhAdNcVvHD0Gz4FkRj5jRAD1aAGQ</textarea>
    </form>
  ```

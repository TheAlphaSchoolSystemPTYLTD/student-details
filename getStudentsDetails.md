**getStudentsDetails**
----
	Returns an array of structured Student data comprising general, school, and other school details in JSON format.

* **Version HIstory:**

  TASS v51.4 - Update Version History to include three added params `pc_tutor_group`, `class`, `year_group`.

  TASS v52.0 - Return 3 new fields `preferred_surname`, `first_name`, `other_name` in general_details.
  
  TASS v54.4 - Return 1 new fields `multiparent_flag` in general_details.

  TASS v55.3 - Return 2 new fields `last_update_on`, `last_update_by` in general_details.
               Add params `update_on_from`, `update_on_to`, `update_on`.

* **Version:**

	3

* **Permission:**

  Student Record > Students > View

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

	`update_on_from` - Date for comparison with the last update date. Data that is greater than `update_on_from` is considered.

	`update_on_to` - Date for comparison with the last update date. Data that is less than `update_on_from` is considered.

	`update_on` - Date for comparison with the last update date. Data that exact match on `update_on_from` is considered.

	**Conditional:**

	none

* **Success Response:**

    ```javascript
      {
        "students": [
          {
            "general_details": {
              "surname": "Clark",
              "next_year_indicator": "Advancing",
              "date_of_leaving": "",
              "student_code": "0009130",
              "usi": "23WRRTHK",
              "preferred_surname": "Clark",
              "first_name": "Andréa",
              "mobile_phone": "0426505880",
              "lui_number": 6669130,
              "entry_year_group": 8,
              "par_code": "000055",
              "sms_flg": "Y",
              "religion": "Anglican",
              "preferred_name": "Andy",
              "other_name": "Joan",
              "gender": "",
              "date_of_entry": "31/03/2018",
              "date_of_birth": "02/09/1994",
              "alternate_id": "%BDMITC?",
              "given_names": "Andréa Joan",
	      	    "multipar_flg ": "Y",
              "last_update_on": "25/03/2021 04:37:50 PM",
              "last_update_by": "Admin"
            },
            "school_details": {
              "campus": "Banana Cmpy 10 Campus",
              "email_address": "testing@tassweb.com.au",
              "pc_tutor_group": "9DD",
              "boarder": "Yes",
              "student_cafe_access": "Yes",
              "house": "Banksia",
              "year_group": 11,
              "form_class": "F",
              "residency_status": "Australian Citizen"
            },
            "other_school_details": {
              "nationality": "Australian",
              "early_depature": "Y",
              "parish": "Chermside",
              "learning_problems": "Y",
              "extra_tuition": "N",
              "returning_student": "Y",
              "medical_condition": "None",
              "sprecken_sie_deutche": "",
              "campus": "St Hilda's",
              "alpha_code": "",
              "locker_number": 221,
              "private_insurance": "N",
              "lives_with": "Father",
              "bus_route": "Shopping Town",
              "country_of_birth": "Australia",
              "passport_number/date": "AU544554",
              "rail_station": "Central",
              "visa_number/date": "1234567890qwertuiopa",
              "residential_house": "Harris",
              "late_arrival": "N",
              "repeat_year": 1,
              "aaspa_address": "Y",
              "address_home": "Female",
              "external_tuition": "N",
              "application_date": "1999/11"
            }
          }
        ],
         "__tassversion": "01.055.3.000",
        "token": {
        "code": "0009130",
        "timestamp": "{ts '2021-07-27 12:08:49'}",
        "currentstatus": "current"
        }
      }
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
      "code":"0009130"
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

**getCommunicationRulesDetails**
----
  Returns an array of structured Communication Rules data including student code and addresses in JSON format.
    
* **Version History:**

  TASS v51.4 - Add a new Property `addressee`. Erroneous `adressee` field is depreciated and will be removed in a future version.

  TASS v51.4 (PR4) - New Property `email_2` added.

  TASS v52.0 - Return 16 new fields `m_description`, `m_title`, `m_initials`, `m_surname`, `m_first_name`, `m_other_name`, `m_preferred_name`, `m_suffix`, `f_description`, `f_title`, `f_initials`, `f_surname`, `f_first_name`, `f_other_name`, `f_preferred_name`, `f_suffix` for each address.

* **Version:**

  3

* **Permission:**

  Student Records > Students > View

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**

   `currentstatus [string]` -  Must be 'current' or 'future' or 'past' or 'noncurrent'

   `commtype [string]` - Communication Rule Type. Must be one of:
    ```HTML
        all - Communication Types
        aca – Academic Reports
        att – Attendance
        ec – Emergency Contact
        gen – TASS.web Correspondence
        lw – Student Lives With
        tk – Teacher Kiosk View
        tkco – Teacher Kiosk Correspondence
    ```
   
   **Optional:**

   `code [string]` - Student code
 
   **Conditional:**
 
   none

* **Success Response:**

    ```javascript
      {
        "commrules": [
          {
            "addresses": [
              {
                "communication_type": "EC,GEN,LW,TKCO",
                "mobile_phone_2": "",
                "adressee": "Paula Clark",
                "sms_flg_2": "N",
                "m_initials": "P",
                "m_suffix": "suf",
                "m_surname": "Clark",
                "m_description": "Mother/Parent 1",
                "m_preferred_name": "Paula",
                "m_other_name": "PauOth",
                "m_title": "Mrs",
                "m_first_name": "Paula",
                "address_description": "Mother/Parent 1",
                "email_2": "",
                "mobile_phone_1": "0427203657",
                "sms_flg_1": "Y",
                "f_initials": "E",
                "f_suffix": "",
                "f_surname": "Clark",
                "f_description": "Father/Parent 2",
                "f_preferred_name": "Edward",
                "f_other_name": "",
                "f_title": "",
                "f_first_name": "Edward",
                "addressee": "Paula Clark",
                "email": "tester@tassweb.com.au",
                "business_phone": "3201 1302",
                "parent_code": "000055",
                "current_address": "Mrs P Clarké Second Line<br />123 Smith Rd<br />the bag end of nowhere<br />ALBION NT 4005<br />AUSTRALIA",
                "salutation": "Mrs Clark (Mother 6)",
                "home_phone": "3870 9987",
                "relationship": "Step",
                "tag": "Student Lives With / Emergency Contact",
                "facsimile": "375575756576"
              }
            ],
            "studcode": "0009130"
          }
        ],
        "__tassversion": "01.053.3.000",
        "token": {
          "code": "0009130",
          "commtype": "all",
          "timestamp": "{ts '2019-11-27 14:17:27'}",
          "currentstatus": "current"
        }
      }
    ```
 
* **Error Response:**

    `commtype` not supplied
    ```javascript
    __invalid: {
      "commtype": "field is required"
    }
    ```

    `commtype` - Communication Rules must be enabled. 
    ```javascript
    __invalid: {
      "commtype": "Communication Rules are not enabled."
    }
    ```

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
    
* **Sample Parameters:**

  ```javascript
    { 
      "currentstatus":"current",
      "code":"20073",
      "commtype":"all"
    }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=GetCommunicationRulesDetails&appcode=DEMOSD&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getCommunicationRulesDetails">
       <input type="hidden" name="appcode" value="DEMOSD">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```

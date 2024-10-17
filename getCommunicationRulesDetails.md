**getCommunicationRulesDetails**
----
  Returns an array of structured Communication Rules data including student code and addresses in JSON format.
    
* **Version History:**

  TASS v51.4 - Add a new Property `addressee`. Erroneous `adressee` field is depreciated and will be removed in a future version.

  TASS v51.4 (PR4) - New Property `email_2` added.

  TASS v52.0 - Return 16 new fields `m_description`, `m_title`, `m_initials`, `m_surname`, `m_first_name`, `m_other_name`, `m_preferred_name`, `m_suffix`, `f_description`, `f_title`, `f_initials`, `f_surname`, `f_first_name`, `f_other_name`, `f_preferred_name`, `f_suffix` for each address.

  TASS v55.4 (PR3) - Return 4 new fields `address_person_posn`, `address_person_label`, `address_person_gender`, `address_person_gender_desc` for each address.

  TASS v57.11 - Add `add_num`, `m_person_num`,`f_person_num` in returned data

  TASS v58.01 - Add `m_deceased_flg`, `f_deceased_flg` in returned data
  
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
   
   `useoptimised [boolean]` - Use optimised version of the code for better performance (default is true)
 
   **Conditional:**
 
   none

* **Success Response:**

    ```javascript
      {
        "commrules":[
          {
            "addresses":[
              {
                "communication_type":"TK",
                "add_num":6,
                "sms_flg_2":"N",
                "f_deceased_flg ": "N",
                "email_2":"mother2@tassweb.com.au",
                "sms_flg_1":"Y",
                "m_initials":"P",
                "f_preferred_name":"Edward",
                "addressee":"Paula Other and even more names that thomas the Tank Clark",
                "email":"mother@tassweb.com.au",
                "m_deceased_flg ": "N",
                "m_preferred_name":"Paula",
                "m_person_num":30,
                "business_phone":"3201 1302",
                "address_person_gender_desc":"Female",
                "salutation":"Mrs Clark (Mother 6)",
                "m_title":"Ms",
                "m_suffix":"MA",
                "f_suffix":"PA",
                "home_phone":"3870 9987",
                "address_person_label":"Mother/Parent 1",
                "address_person_posn":1,
                "f_surname":"Clark",
                "mobile_phone_2":"yeah yeah",
                "f_initials":"E",
                "adressee":"Paula Other and even more names that thomas the Tank Clark",
                "address_description":"Mother/Parent 1",
                "mobile_phone_1":"0412016500",
                "f_description":"Father/Parent 2",
                "f_other_name":"Other",
                "m_first_name":"Paula",
                "f_title":"Mr",
                "parent_code":"000055",
                "m_description":"Mother/Parent 1",
                "current_address":"Mrs P Clarke Second Line<br />Gigi Lodge<br />Unit 810<br />24 Augustus Street<br />TOOWONG QLD 4066",
                "m_other_name":"Other and even more names that thomas the Tank",
                "f_first_name":"Edward",
                "m_surname":"Clark",
                "f_person_num":29,
                "relationship":"Biological",
                "tag":"",
                "address_person_gender":"F",
                "facsimile":"375575756576"
              },
              {
                "communication_type":"TK",
                "add_num":7,
                "sms_flg_2":"Y",
                "f_deceased_flg ": "N",
                "email_2":"father2@tassweb.com.au",
                "sms_flg_1":"N",
                "m_initials":"P",
                "f_preferred_name":"Edward",
                "addressee":"Edward Edward Clark",
                "email":"father@tassweb.com.au",
                "m_deceased_flg ": "N",
                "m_preferred_name":"Paula",
                "m_person_num":30,
                "business_phone":"33201 1301",
                "address_person_gender_desc":"Male",
                "salutation":"Mr Clark (Father 7)",
                "m_title":"Ms",
                "m_suffix":"MA",
                "f_suffix":"PA",
                "home_phone":"3870 9987",
                "address_person_label":"Father/Parent 2",
                "address_person_posn":2,
                "f_surname":"Clark",
                "mobile_phone_2":"0412016500",
                "f_initials":"E",
                "adressee":"Edward Edward Clark",
                "address_description":"Father/Parent 2",
                "mobile_phone_1":"",
                "f_description":"Father/Parent 2",
                "f_other_name":"Other",
                "m_first_name":"Paula",
                "f_title":"Mr",
                "parent_code":"000055",
                "m_description":"Mother/Parent 1",
                "current_address":"Mr E.&R Clark# A.K.A %%Wellington<br />Somerset Park<br />Unit 54<br />2-4 Langport Parade<br />MUDGEERABA QLD 4213",
                "m_other_name":"Other and even more names that thomas the Tank",
                "f_first_name":"Edward",
                "m_surname":"Clark",
                "f_person_num":29,
                "relationship":"Former",
                "tag":"",
                "address_person_gender":"M",
                "facsimile":"33201 5545"
              }
            ],
            "studcode":"0009130"
          }
        ],
        "__tassversion": "01.057.11.000",
        "token":{
          "code":"0009130",
          "commtype":"all",
          "timestamp":"{ts '2022-09-28 11:44:31'}",
          "currentstatus":"current"
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

**getCommunicationRulesDetails**
----
  Returns an array of structured Communication Rules data including student code and addresses in JSON format.

* **Version:**

  2

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
      "commrules":[  
        {  
          "addresses":[  
            {  
               "communication_type":"ACA,ATT,EC,GEN,LW,TK,TKCO",
               "mobile_phone_2":"",
               "adressee":"Joan Angus",
               "addressee":"Joan Angus",
               "sms_flg_2":"N",
               "address_description":"Parent\/Caregiver 1",
               "mobile_phone_1":"",
               "sms_flg_1":"N",
               "email":"angus@somewhere.com.au",
               "business_phone":"848 2256",
               "parent_code":10010,
               "current_address":"Ms. J. Angus<br \/>U 4\/6 Emerald St<br \/>KEDRON QLD 4031",
               "salutation":"Ms Angus",
               "home_phone":"3366 2541 Mobile: 015 667 8349",
               "relationship":"Biological",
               "tag":"Student Lives With \/ Emergency Contact",
               "facsimile":"848 4444"
            },
            {  
               "communication_type":"ACA,ATT,EC,GEN,LW,TK,TKCO",
               "mobile_phone_2":"",
               "adressee":"Ronald Angus",
               "addressee":"Ronald Angus",
               "sms_flg_2":"N",
               "address_description":"Parent\/Caregiver 2",
               "mobile_phone_1":"",
               "sms_flg_1":"N",
               "email":"angusr@somewhere.com.au",
               "business_phone":"3987 2345",
               "parent_code":10010,
               "current_address":"Mr. Ronald Angus<br \/>23 Pilliga St<br \/>WAVELL HEIGHTS QLD 4012",
               "salutation":"Mr R Angus",
               "home_phone":"3212 4567",
               "relationship":"Biological",
               "tag":"Student Lives With \/ Emergency Contact",
               "facsimile":"3987 5432"
            },
            {  
               "communication_type":"GEN,TK,TKCO",
               "mobile_phone_2":"",
               "adressee":"Ms. J. Angus ",
               "addressee":"Ms. J. Angus ",
               "sms_flg_2":"N",
               "address_description":"Correspondence",
               "mobile_phone_1":"0413443650",
               "sms_flg_1":"Y",
               "email":"clarks@somewhere.com.au",
               "business_phone":"848 2256",
               "parent_code":10010,
               "current_address":"Ms. J. Angus<br \/>PO Box 3088<br \/>CHERMSIDE WEST QLD 4032",
               "salutation":"Ms Angus",
               "home_phone":"3366 2541 Mobile: 015 667 8349",
               "relationship":"",
               "tag":"",
               "facsimile":"848 4444"
            }
          ],
          "studcode":20073
        }
      ]
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
    http://api.tasscloud.com.au/tassweb/api/?method=GetCommunicationRulesDetails&appcode=DEMOSD&company=10&v=2&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getCommunicationRulesDetails">
       <input type="hidden" name="appcode" value="DEMOSD">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```

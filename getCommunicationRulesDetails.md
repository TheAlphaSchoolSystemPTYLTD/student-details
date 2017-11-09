**getCommunicationRulesDetails**
----
  Returns an array of structured Communication Rules data comprising parent and address details in JSON format.

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
        ???????
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
      "code":"0009130",
      "commtype":"all"
    }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getCommunicationRulesDetails&appcode=DEMOSD&company=10&v=2&token=???????
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/api/">
       <input type="hidden" name="method" value="getCommunicationRulesDetails">
       <input type="hidden" name="appcode" value="DEMOSD">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">???????</textarea>
    </form>
  ```

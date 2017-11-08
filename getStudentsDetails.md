**getStudentsDetails**
----
  Returns an array of structured Student data comprising general, school, and other school details in JSON format.

* **Version:**

  2

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**

   `currentstatus [string]` -  Must be 'current' or 'future' or 'past' or 'noncurrent'
   
   **Optional:**

   `code [string]` - Student code
   
   `includephoto [boolean]` -  Must be 'true' or 'false' for whether returning student photo.

   `thumbnail [boolean]` -  Must be 'true' or 'false' for whether returning student thumbnail photo.

   **Conditional:**
 
   none

* **Success Response:**

    ```javascript
        ???????
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
    
* **Sample Parameters:**

  ```javascript
    { 
      "currentstatus":"current",
      "code":"0009130",
      "includephoto":"true",
      "thumbnail":"true"
    }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getStudentsDetails&appcode=DEMOSD&company=10&v=2&token=???????
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/api/">
       <input type="hidden" name="method" value="getStudentsDetails">
       <input type="hidden" name="appcode" value="DEMOSD">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">???????</textarea>
    </form>
  ```
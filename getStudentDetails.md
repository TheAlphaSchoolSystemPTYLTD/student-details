**getStudentDetails**
----
  Returns a structured Student data comprising general, school, boarder, and mceecdya details in JSON format.

* **Version:**

  2

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**

   `code [string]` - Student code
   
   **Optional:**
   
   `includephoto [boolean]` -  Must be 'true' or 'false' for whether returning student photo.

   `thumbnail [boolean]` -  Must be 'true' or 'false' for whether returning student thumbnail photo.

   **Conditional:**
 
   none

* **Success Response:**

    ```javascript
        ???????
    ```
 
* **Error Response:**

    `code` not supplied
    ```javascript
    __invalid: {
      "code": "field is required"
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
      "code":"0009130",
      "includephoto":"true",
      "thumbnail":"true"
    }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getStudentDetails&appcode=DEMOSD&company=10&v=2&token=???????
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/api/">
       <input type="hidden" name="method" value="getStudentDetails">
       <input type="hidden" name="appcode" value="DEMOSD">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">???????</textarea>
    </form>
  ```

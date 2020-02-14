**getStudentUD**
----
  Returns structured UD data in JSON format.
  
* **Version History:**

  TASS v52.2 - Method Added

* **Version:**

  3

* **Permission:**

  Student Records > Students > View

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**

   `code [string]` - Student code
   
   **Optional:**

   none
 
   **Conditional:**
 
   none

* **Success Response:**

    ```javascript
      { 
         "token":{ 
            "code":"0009130",
            "timestamp":"{ts '2020-02-14 13:36:41'}"
         },
         "ud":{ 
            "ud13_code":"N",
            "ud21_text":"1234567890qwertuiopa",
            "ud16_code":"01",
            "ud4_flg":"N",
            "ud24_text":"Female",
            "ud9_flg":"Y",
            "ud19_code":"HA",
            "ud18_code":"F",
            "ud23_text":221,
            "ud5_flg":"Y",
            "ud12_code":"CHE",
            "ud15_code":"AUS",
            "ud20_code":"",
            "ud1_flg":1,
            "ud7_flg":"Y",
            "ud6_flg":"N",
            "ud10_flg":"",
            "ud22_text":"AU544554",
            "ud25_text":"1999/11",
            "ud14_code":"SHO",
            "ud11_code":"SHI",
            "ud2_flg":"N",
            "ud3_flg":"Y",
            "ud8_flg":"N",
            "ud17_code":"AUS"
         }
      }
    ```
 
* **Error Response:**

    `code` not supplied
    ```javascript
      "__msg": "'code' IS REQUIRED"
    ```
    
* **Sample Parameters:**

  ```javascript
    {"code":"0009130"}
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getStudentUD&appcode=DEMOSD&company=10&v=2&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getStudentUD">
       <input type="hidden" name="appcode" value="DEMOSD">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```

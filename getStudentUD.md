**getStudentUD**
----
  Returns structured UD data in JSON format.
  
* **Version History:**

  TASS v52.2 - Method Added

  TASS v54.0 - Add a new conditional field `currentstatus`, change the required field `studcode` to a conditional field. Add new validations for `studcode` and `currentstatus`.

* **Version:**

  3

* **Permission:**

  Student Records > Students > View

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
   None

   **Optional:**

   None

   **Conditional:**

    `currentstatus [string]` - Required if `code` is not supplied. Must be 'current' or 'future' or 'past' or 'noncurrent'.

    `code [string]` - Student Code. Required if `currentstatus` is not supplied. Contains Only One Student Code if supplied.

* **Success Response:**

    when `currentstatus` is supplied
    ```javascript
    {
        "data":[
            {
                "studcode":"0009130",
                "ud":{
                    "ud13_code":"N",
                    "ud21_text":"1234567890qwertuiopa",
                    "ud16_code":"01",
                    "ud4_flg":"N",
                    "ud24_text":"FemaleOnePlus",
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
            },
            {
                "studcode":"0009134",
                "ud":{
                    "ud13_code":"",
                    "ud21_text":"",
                    "ud16_code":"",
                    "ud4_flg":"",
                    "ud24_text":"Female",
                    "ud9_flg":"",
                    "ud19_code":"",
                    "ud18_code":"",
                    "ud23_text":"",
                    "ud5_flg":"",
                    "ud12_code":"",
                    "ud15_code":"",
                    "ud20_code":"",
                    "ud1_flg":"",
                    "ud7_flg":"",
                    "ud6_flg":"",
                    "ud10_flg":"",
                    "ud22_text":"",
                    "ud25_text":"",
                    "ud14_code":"",
                    "ud11_code":"",
                    "ud2_flg":"",
                    "ud3_flg":"",
                    "ud8_flg":"",
                    "ud17_code":""
                }
            }
        ],
        "__tassversion":"01.000.043.0",
        "token":{
            "timestamp":"{ts '2020-11-12 09:45:07'}",
            "currentstatus":"current"
        }
    }
    ```

    when only `code` is supplied
    ```javascript
    {
        "__tassversion":"01.000.043.0",
        "token":{
            "code":"0009130",
            "timestamp":"{ts '2020-11-12 09:43:00'}"
        },
        "ud":{
            "ud13_code":"N",
            "ud21_text":"1234567890qwertuiopa",
            "ud16_code":"01",
            "ud4_flg":"N",
            "ud24_text":"FemaleOnePlus",
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

    `code` and `currentstatus` are both not supplied
    ```javascript
      "error": "code or currentstatus is required."
    ```

    `code` contains more than one student code
    ```javascript
      "error": "Only one code can be processed at a time."
    ```

    `code` does not exist in `currentstatus` student list
    ```javascript
      "error": "[code] is not a valid [currentstatus] student."
    ```

    `currentstatus` does not match 'current' or 'future' or 'past' or 'noncurrent'
    ```javascript
      "error": "[currentstatus] must be 'current' or 'future' or 'past' or 'noncurrent'."
    ```

* **Sample Parameters:**

    when `currentstatus` is supplied
  ```javascript
    {
      "currentstatus":"current"
    }
  ```

    when only `code` is supplied
  ```javascript
    {
      "code":"0009130"
    }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getStudentUD&appcode=DEMOSD&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getStudentUD">
       <input type="hidden" name="appcode" value="DEMOSD">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```

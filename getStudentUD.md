**getStudentUD**
----
  Returns structured UD data in JSON format.
  
* **Version History:**

  TASS v52.2 - Method Added

  TASS v53.3 PR TBD - Add a new conditional field `currentstatus`, change the required field `studcode` to a conditional field. Add validation for `studcode` and `currentstatus`.

* **Version:**

  3

* **Permission:**

  Student Records > Students > View

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**

   none
   
   **Optional:**

   none
 
   **Conditional:**
 
   `currentstatus [string]` - Required if `code` is not supplied. Must be 'current' or 'future' or 'past' or 'noncurrent'.
 
   `code [string]` - Required if `currentstatus` is not supplied. Contains Only One Code if supplied.

* **Success Response:**

    when only `code` is supplied
    ```javascript
      {
        "ud": {
          "ud13_code": "N",
          "ud21_text": "1234567890qwertuiopa",
          "ud16_code": "01",
          "ud4_flg": "N",
          "ud24_text": "Female",
          "ud9_flg": "Y",
          "ud19_code": "HA",
          "ud18_code": "F",
          "ud23_text": 221,
          "ud5_flg": "Y",
          "ud12_code": "CHE",
          "ud15_code": "AUS",
          "ud20_code": "",
          "ud1_flg": 1,
          "ud7_flg": "Y",
          "ud6_flg": "N",
          "ud10_flg": "",
          "ud22_text": "AU544554",
          "ud25_text": "1999/11",
          "ud14_code": "SHO",
          "ud11_code": "SHI",
          "ud2_flg": "N",
          "ud3_flg": "Y",
          "ud8_flg": "N",
          "ud17_code": "AUS"
        },
        "__tassversion": "01.053.3.000",
        "token": {
          "code": "0009130",
          "timestamp": "{ts '2021-01-21 12:30:59'}"
        }
      }
    ```

    when only `currentstatus` is supplied
    ```javascript
    {
      "data": [
        {
          "studcode": "0009129",
          "ud": {
            "ud13_code": "AST",
            "ud21_text": "5342 92528 1",
            "ud16_code": "",
            "ud4_flg": "Y",
            "ud24_text": "Male",
            "ud9_flg": "N",
            "ud19_code": "",
            "ud18_code": "M",
            "ud23_text": 109,
            "ud5_flg": "Y",
            "ud12_code": "STA",
            "ud15_code": "AUS",
            "ud20_code": "",
            "ud1_flg": "N",
            "ud7_flg": "N",
            "ud6_flg": "N",
            "ud10_flg": "",
            "ud22_text": "",
            "ud25_text": "",
            "ud14_code": "DON",
            "ud11_code": "SMA",
            "ud2_flg": "N",
            "ud3_flg": "Y",
            "ud8_flg": "N",
            "ud17_code": ""
          }
        },
        {
          "studcode": "0009130",
          "ud": {
            "ud13_code": "N",
            "ud21_text": "1234567890qwertuiopa",
            "ud16_code": "01",
            "ud4_flg": "N",
            "ud24_text": "Female",
            "ud9_flg": "Y",
            "ud19_code": "HA",
            "ud18_code": "F",
            "ud23_text": 221,
            "ud5_flg": "Y",
            "ud12_code": "CHE",
            "ud15_code": "AUS",
            "ud20_code": "",
            "ud1_flg": 1,
            "ud7_flg": "Y",
            "ud6_flg": "N",
            "ud10_flg": "",
            "ud22_text": "AU544554",
            "ud25_text": "1999/11",
            "ud14_code": "SHO",
            "ud11_code": "SHI",
            "ud2_flg": "N",
            "ud3_flg": "Y",
            "ud8_flg": "N",
            "ud17_code": "AUS"
          }
        }
      ],
      "__tassversion": "01.053.3.000",
      "token": {
        "timestamp": "{ts '2021-01-21 12:32:43'}",
        "currentstatus": "current"
      }
    }
    ```
 
* **Error Response:**

    `code` and `currentstatus` are both not supplied
    ```javascript
      "error": "code or currentstatus is required."
    ```

    `code` contains more than one code
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
    {"currentstatus":"current"}
  ```

    when `code` is supplied
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

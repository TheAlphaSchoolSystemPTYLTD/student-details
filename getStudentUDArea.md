**getStudentUDArea**
----
  Returns structured UD area data in JSON format.
  
* **Version History:**

  TASS v52.2 - Method Added

* **Version:**

  3

* **Permission:**

  Student Records > Students > UD Areas tab > View

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**

   `code [string]` - Student Code

   `areacode [string]` - Area Code
   
   **Optional:**

   none
 
   **Conditional:**
 
   none

* **Success Response:**

    ```javascript
      { 
        "__tassversion": "01.053.3.000",
         "token":{ 
            "code":"0009130",
            "areacode":1,
            "timestamp":"{ts '2021-01-21 12:39:08'}"
         },
         "ud":{ 
            "ud13_code":"",
            "ud21_text":"",
            "ud16_code":"CIT",
            "ud4_flg":"",
            "ud27_text":"",
            "ud24_text":"",
            "ud9_flg":"",
            "ud38_date":"",
            "ud32_date":"",
            "ud19_code":"",
            "ud35_date":"",
            "ud29_text":"",
            "ud26_text":"",
            "ud30_text":"",
            "ud18_code":"",
            "ud23_text":"",
            "ud5_flg":"",
            "ud12_code":"",
            "ud20_code":"",
            "ud15_code":"",
            "ud1_flg":"N",
            "ud31_date":"2016-03-23 00:00:00.0",
            "ud34_date":"",
            "ud37_date":"",
            "ud7_flg":"",
            "ud28_text":"",
            "ud10_flg":"",
            "ud6_flg":"",
            "ud22_text":"",
            "ud25_text":"",
            "ud14_code":"",
            "ud11_code":"",
            "ud2_flg":"",
            "ud3_flg":"",
            "ud40_date":"",
            "ud33_date":"",
            "ud8_flg":"",
            "ud17_code":"",
            "ud36_date":"",
            "ud39_date":"",
            "update_on":"2019-10-22 14:13:00.0"
         }
      }
    ```
 
* **Error Response:**

    `code` not supplied
    ```javascript
      "__msg": "'code' IS REQUIRED"
    ```

    `areacode` not supplied
    ```javascript
      "__msg": "'areacode' IS REQUIRED"
    ```

    `areacode` not integer
    ```javascript
      "__msg": "'areacode' MUST BE AN INTEGER"
    ```
    
* **Sample Parameters:**

  ```javascript
    {"code":"0009130","areacode":"1"}
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getStudentUDArea&appcode=DEMOSD&company=10&v=2&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getStudentUDArea">
       <input type="hidden" name="appcode" value="DEMOSD">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```

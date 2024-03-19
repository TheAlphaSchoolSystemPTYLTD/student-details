**getStudentsUDArea**
----
  Returns an array of all structured students' UD area data in JSON format.
  
* **Version History:**

  TASS v57.10 - Method Added

* **Version:**

  3

* **Permission:**

  Student Records > Students > UD Areas tab > View

* **Method:**

  `GET | POST`
  
* **Params:**

  **Required:**

  `areacode [string]` - Area Code
  
  **Optional:**

  none
 
  **Conditional:**

  `currentstatus [string]` - Required if `studcode` is not supplied. Must be 'current' or 'future' or 'past' or 'noncurrent'.

  `studcode [string]` - Required if `currentstatus` is not supplied. Contains a list of Student Code(s) if supplied.

* **Success Response:**

    ```javascript
    {
      "data":[
        {
          "ud13_code":"",
          "ud21_text":"testing",
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
          "ud1_flg":"P",
          "ud31_date":"2019-02-08 00:00:00.0",
          "ud34_date":"",
          "ud37_date":"",
          "ud7_flg":"",
          "ud28_text":"",
          "ud10_flg":"",
          "ud6_flg":"",
          "ud22_text":"",
          "ud25_text":"",
          "ud14_code":"GLB",
          "ud11_code":10,
          "ud2_flg":3,
          "ud3_flg":"",
          "ud40_date":"",
          "stud_code":"0009130",
          "ud33_date":"",
          "ud8_flg":"",
          "ud17_code":"",
          "ud36_date":"",
          "ud39_date":""
        },
        {
          "ud13_code":"",
          "ud21_text":"",
          "ud16_code":"",
          "ud4_flg":"N",
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
          "ud1_flg":"Y",
          "ud31_date":"",
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
          "stud_code":"0009131",
          "ud33_date":"",
          "ud8_flg":"",
          "ud17_code":"",
          "ud36_date":"",
          "ud39_date":""
        }
      ],
      "__tassversion":"01.057.10.100",
      "token":{
        "areacode":1,
        "timestamp":"{ts '2022-08-17 21:54:36'}",
        "studcode":"0009130,0009131"
      }
    }
    ```
 
* **Error Response:**

    `areacode` not supplied
    ```javascript
      "__msg": "'areacode' IS REQUIRED"
    ```

    `areacode` not integer
    ```javascript
      "__msg": "'areacode' MUST BE AN INTEGER"
    ```

    `studcode` and `currentstatus` are both not supplied
    ```javascript
      "error": "studcode or currentstatus is required."
    ```

    `currentstatus` does not match 'current' or 'future' or 'past' or 'noncurrent'
    ```javascript
      "error": "[currentstatus] must be 'current' or 'future' or 'past' or 'noncurrent'."
    ```

    `studcode` does not exist in `currentstatus` student list
    ```javascript
      "error": "[studcode] is not a valid [currentstatus] student."
    ```
    
* **Sample Parameters:**

  ```javascript
    {
      "areacode":"1",
      "studcode":"0009130,0009131",
      "currentstatus":"current"
    }
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getStudentsUDArea&appcode=DEMOSD&company=10&v=2&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getStudentsUDArea">
       <input type="hidden" name="appcode" value="DEMOSD">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```

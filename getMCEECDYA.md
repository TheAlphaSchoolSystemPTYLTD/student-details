**getMCEECDYA**
----
  Returns structured MCEECDYA data in JSON format.
  
* **Version History:**

  TASS v53.0 - Method Added

* **Version:**

  3

* **Permission:**

  Student Records > Students > MCEECDYA (tab)

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**

   `studcode [string]` - Student Code

   **Optional:**

   none
 
   **Conditional:**
 
   none

* **Success Response:**

    ```javascript
    {
        "FOCC_CODE":{
            "code":"FOCC_CODE",
            "desc":9
        },
        "MLOTE_CODE":{
            "code":"MLOTE_CODE",
            "desc":9302
        },
        "FSE_CODE":{
            "code":"FSE_CODE",
            "desc":0
        },
        "SLOTE_CODE":{
            "code":"SLOTE_CODE",
            "desc":9301
        },
        "UPDATE_BY":{
            "code":"UPDATE_BY",
            "desc":"fang"
        },
        "MOCC_CODE":{
            "code":"MOCC_CODE",
            "desc":9
        },
        "SCOB_CODE":{
            "code":"SCOB_CODE",
            "desc":8000
        },
        "ARRIVE_YR":{
            "code":"ARRIVE_YR",
            "desc":2014
        },
        "S_INDIG_STS":{
            "code":"S_INDIG_STS",
            "desc":9
        },
        "FLOTE_CODE":{
            "code":"FLOTE_CODE",
            "desc":9303
        },
        "MSE_CODE":{
            "code":"MSE_CODE",
            "desc":0
        },
        "MNSE_CODE":{
            "code":"MNSE_CODE",
            "desc":0
        },
        "FNSE_CODE":{
            "code":"FNSE_CODE",
            "desc":0
        },
        "token":{
            "timestamp":"{ts '2020-05-22 08:31:45'}",
            "studcode":"0021218"
        },
        "UPDATE_ON":{
            "code":"UPDATE_ON",
            "desc":"2020-05-21 00:00:00.0"
        }
    }
    ```
 
* **Error Response:**

    `studcode` not supplied
    ```javascript
      "__invalid": {
        "error": "studcode is required."
      }
    ```

    `studcode` not exist in MCEECDYA record
    ```javascript
      "__invalid": {
        "error": "studcode not exist in MCEECDYA."
      }
    ```
    
* **Sample Parameters:**

  ```javascript
    {"studcode":"0021218"}
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getMCEECDYA&appcode=API12&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMCEECDYA">
       <input type="hidden" name="appcode" value="API12">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```

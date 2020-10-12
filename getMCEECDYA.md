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
      "student":{
          "S_INDIG_STS":{
              "code":9,
              "desc":"Unknown"
          },
          "SLOTE_CODE":{
              "code":9301,
              "desc":"Fijian"
          },
          "SCOB_CODE":{
              "code":8000,
              "desc":"AMERICAS"
          },
          "ARRIVE_YR":{
              "code":2014,
              "desc":"ARRIVE_YR"
          }
      },
      "parent1":{
          "MLOTE_CODE":{
              "code":9302,
              "desc":"Gilbertese"
          },
          "MSE_CODE":{
              "code":0,
              "desc":"Not stated/unknown"
          },
          "MNSE_CODE":{
              "code":0,
              "desc":"Not stated/unknown"
          },
          "MOCC_CODE":{
              "code":9,
              "desc":9
          }
      },
      "parent2":{
          "FOCC_CODE":{
              "code":9,
              "desc":9
          },
          "FSE_CODE":{
              "code":0,
              "desc":"Not stated/unknown"
          },
          "FLOTE_CODE":{
              "code":9303,
              "desc":"Maori (Cook Island)"
          },
          "FNSE_CODE":{
              "code":0,
              "desc":"Not stated/unknown"
          }
      },
      "token":{
          "timestamp":"{ts '2020-05-25 09:02:16'}",
          "studcode":"0021218"
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

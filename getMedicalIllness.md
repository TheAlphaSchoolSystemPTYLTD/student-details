**getMedicalIllness**
----
  Returns a structured student medical illness details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

* **Version:**

  3

* **Permission:**

  Medical Setup > Student Medical > Student Illness/Daily Log > View

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
    `studcode` [string] - Student Code

    `ill_date` [date] - Illness Data

    `ill_time` [time] - Illness Time

    `mcond_code` [string] - Medical Condition Code

   **Optional:**

   None

   **Conditional:**

   None

* **Success Response:**

    ```javascript
    {
      "ill_time": "1900-01-01 08:49:00.0",
      "ill_desc": "Fell while skating on thin ice",
      "ill_date": "2019-04-12 00:00:00.0",
      "host_flg": "N",
      "mcond_desc": "Accident",
      "desc": "Ice applied",
      "treat_code": "ICE",
      "medication_text": "",
      "note_text": "",
      "disch_date": "",
      "mcond_code": "ACC",
      "disch_time": "",
      "__tassversion": "01.053.3.000",
      "token": {
        "ill_time": "08:49:00.0",
        "timestamp": "{ts '2021-01-19 16:22:50'}",
        "studcode": "0009130",
        "mcond_code": "ACC",
        "ill_date": "2019-04-12"
      }
    }
    ```
 
* **Error Response:**

    `studcode` not supplied
    ```javascript
      "error": "studcode is required."
    ```

    `ill_date` not supplied
    ```javascript
      "error": "ill_date is required."
    ```

    `ill_time` not supplied
    ```javascript
      "error": "ill_time is required."
    ```

    `mcond_code` not supplied
    ```javascript
      "error": "mcond_code is required."
    ```

* **Sample Parameters:**

  ```javascript
    {"studcode":"0009130","ill_date":"2019-04-12","ill_time":"08:49:00.0","mcond_code": "ACC"}
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getMedicalIllness&appcode=API10&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMedicalIllness">
       <input type="hidden" name="appcode" value="API10">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```
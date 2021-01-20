**getMedicalAsthmaManagement**
----
  Returns a structured student medical Asthma management details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

  TASS v53.3 PR TBD - Add a new conditional field `currentstatus`, change the required field `studcode` to a conditional field. Add new validations for `studcode` and `currentstatus`.

* **Version:**

  3

* **Permission:**

  Medical Setup > Student Medical > Asthma Management tab > View

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
   None

   **Optional:**

   None

   **Conditional:**

    `currentstatus [string]` - Required if `studcode` is not supplied. Must be 'current' or 'future' or 'past' or 'noncurrent'.

    `studcode [string]` - Required if `currentstatus` is not supplied. Contains Only One Student Code if supplied.

* **Success Response:**

    when `studcode` is supplied
    ```javascript
    {
      "data": [
        {
          "asthma_usual_signs": {
          "speak_flg": "N",
          "breath_flg": "Y",
          "wheez_flg": "Y",
          "comm_text": "You can always tell when Andrea is having an Asthma attack.  First she starts wheezing like an old steam train.  This could go on for some time and become quite significant.  Sometimes she coughs x200",
          "tight_flg": "Y",
          "cough_flg": "N"
        },
          "asthma_triggers": {
          "cold_virus_flg": "N",
          "pollen_flg": "Y",
          "food_text": "",
          "food_flg": "Y",
          "dust_flg": "N",
          "comm_text": "Is partial to attacks in August, September, October, November, December and January.  However she is also prone to attacks in February, March, April, May, June and July.  The weather also impacts x200",
          "exercise_flg": "Y"
        },
          "asthma_worsening_signs": {
          "speak_flg": "N",
          "breath_flg": "N",
          "wheez_flg": "Y",
          "comm_text": "You can tell that her Asthma is getting worse when she turns blue in the face.  It is really such a striking blue colour, you can't possible miss it.  She may also pass out and fall down.  You canx200",
          "tight_flg": "N",
          "cough_flg": "Y"
          },
          "studcode": "0009130"
        }
      ],
      "__tassversion": "01.000.043.0",
      "token": {
        "timestamp": "{ts '2021-01-20 09:34:51'}",
        "studcode": "0009130"
      }
    }
    ```

    when `currentstatus` is supplied
    ```javascript
    {
      "data": [
        {
          "asthma_usual_signs": {},
          "asthma_triggers": {},
          "asthma_worsening_signs": {},
          "error": "This student does not have asthma as a medical condition.",
          "studcode": "0009129"
        },
        {
          "asthma_usual_signs": {
            "speak_flg": "N",
            "breath_flg": "Y",
            "wheez_flg": "Y",
            "comm_text": "You can always tell when Andrea is having an Asthma attack.  First she starts wheezing like an old steam train.  This could go on for some time and become quite significant.  Sometimes she coughs x200",
            "tight_flg": "Y",
            "cough_flg": "N"
          },
          "asthma_triggers": {
            "cold_virus_flg": "N",
            "pollen_flg": "Y",
            "food_text": "",
            "food_flg": "Y",
            "dust_flg": "N",
            "comm_text": "Is partial to attacks in August, September, October, November, December and January.  However she is also prone to attacks in February, March, April, May, June and July.  The weather also impacts x200",
            "exercise_flg": "Y"
          },
          "asthma_worsening_signs": {
            "speak_flg": "N",
            "breath_flg": "N",
            "wheez_flg": "Y",
            "comm_text": "You can tell that her Asthma is getting worse when she turns blue in the face.  It is really such a striking blue colour, you can't possible miss it.  She may also pass out and fall down.  You canx200",
            "tight_flg": "N",
            "cough_flg": "Y"
          },
        "studcode": "0009130"
        },
      ],
      "__tassversion": "01.053.3.000",
      "token": {
        "timestamp": "{ts '2021-01-20 11:49:16'}",
        "currentstatus": "current"
      }
    }
    ```
 
* **Error Response:**

    `studcode` and `currentstatus` are both not supplied
    ```javascript
      "error": "studcode or currentstatus is required."
    ```

    `studcode` contains more than one student code
    ```javascript
      "error": "Only one studcode can be processed at a time."
    ```

    `studcode` does not exist in `currentstatus` student list
    ```javascript
      "error": "[studcode] is not a valid [currentstatus] student."
    ```

    `currentstatus` does not match 'current' or 'future' or 'past' or 'noncurrent'
    ```javascript
      "error": "[currentstatus] must be 'current' or 'future' or 'past' or 'noncurrent'."
    ```

* **Sample Parameters:**
    when `studcode` is supplied
  ```javascript
    {"studcode":"0009130"}
  ```

    when `currentstatus` is supplied
  ```javascript
    {"currentstatus":"current"}
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getMedicalAsthmaManagement&appcode=API10&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMedicalAsthmaManagement">
       <input type="hidden" name="appcode" value="API10">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```
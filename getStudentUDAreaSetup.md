**getStudentUDAreaSetup**
----
  Returns structured UD setup data in JSON format.
  
* **Version History:**

  TASS v52.2 - Method Added

* **Version:**

  3

* **Permission:**

  Student Records > Student Records Setup > UD Areas tab > View

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**

   `includelookups [boolean]` - Include Look Up Details

   **Optional:**

   `areacode [number]` - Area Code
 
   **Conditional:**
 
   none

* **Success Response:**

    when only `includelookups` is supplied
    ```javascript
      { 
         "ud_area":[
            { 
               "area_desc":"Student Stengths",
               "area_code":0
            },
            { 
               "area_desc":"Transport",
               "area_code":1
            },
            { 
               "area_desc":"Parent Access",
               "area_code":2
            },
            { 
               "area_desc":"Learning Needs",
               "area_code":3
            },
            { 
               "area_desc":"Seasonal SportXXX",
               "area_code":4
            },
            { 
               "area_desc":"Enrolment Testing",
               "area_code":5
            },
            { 
               "area_desc":"Enterprise Student Ranking",
               "area_code":500
            },
            { 
               "area_desc":"Enterprise UD Area",
               "area_code":501
            },
            { 
               "area_desc":"Siblings In Other School",
               "area_code":6
            }
         ],
         "__tassversion": "01.053.3.000",
         "token":{ 
            "includelookups":true,
            "timestamp": "{ts '2021-01-21 12:57:23'}"
         }
      }
    ```

    when both `areacode` and `includelookups` are supplied
    ```javascript
    {
      "ud_area": [
        {
          "eudfld1_desc": "Good at Math",
          "area_code": 0,
          "lookups": [],
          "eudfld1_trig": "Y",
          "eudfld1_sort": 7
        },
        {
          "eudfld11_sort": 6,
          "eudfld11_trig": 10,
          "area_code": 0,
          "lookups": [
            {
              "code": 10,
              "desc": "Love"
            },
            {
              "code": 2,
              "desc": "To define this reference data takes many character"
            },
            {
              "code": 5,
              "desc": "Perspective"
            },
            {
              "code": "QUA",
              "desc": "Qualitative Program"
            }
          ],
          "eudfld11_desc": "Reference Data"
        },
        {
          "eudfld21_desc": "Comment",
          "eudfld21_trig": "danke",
          "area_code": 0,
          "eudfld21_sort": 5,
          "lookups": []
        },
        {
          "eudfld22_desc": "Long Trigger",
          "area_code": 0,
          "eudfld22_trig": "The quick brown fox jumped over the lazy pig",
          "lookups": [],
          "eudfld22_sort": 2
        }
      ],
      "area_code": 0,
      "__tassversion": "01.053.3.000",
      "token": {
        "includelookups": true,
        "areacode": 0,
        "timestamp": "{ts '2021-01-21 13:06:00'}"
      }
    }
    ```
 
* **Error Response:**

    `includelookups` not supplied
    ```javascript
      "__invalid": {
        "includelookups": "field is required"
      }
    ```
    
* **Sample Parameters:**

  ```javascript
    {"includelookups":"true", "areacode":"0"}
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getStudentUDAreaSetup&appcode=DEMOSD&company=10&v=2&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getStudentUDAreaSetup">
       <input type="hidden" name="appcode" value="DEMOSD">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```

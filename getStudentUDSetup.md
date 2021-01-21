**getStudentUDSetup**
----
  Returns structured UD setup data in JSON format.
  
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

   `includelookups [boolean]` - Include Look Up Details

   **Optional:**

   none
 
   **Conditional:**
 
   none

* **Success Response:**

    ```javascript
      { 
        "__tassversion": "01.053.3.000",
         "token":{ 
            "includelookups":true,
            "timestamp": "{ts '2021-01-21 13:13:07'}"
         },
         "ud":[ 
            { 
               "flag_name":"UD1_DESC",
               "id":1,
               "flag_value":"Repeat Year",
               "desc":"Repeat Year",
               "name":"UD1_DESC"
            },
            {UD[2-9]_DESC},
            { 
               "flag_name":"UD10_DESC",
               "id":10,
               "flag_value":"Sprecken Sie Deutche",
               "desc":"Sprecken Sie Deutche",
               "name":"UD10_DESC"
            },
            { 
               "flag_name":"UD11_DESC",
               "id":11,
               "lookups":[ 
                  { 
                     "code":"ARG",
                     "desc":"Argyle St"
                  },
                  { 
                     "code":"AST",
                     "desc":"Asplet Terrace"
                  },
                  { 
                     "code":"BH",
                     "desc":"Bisbane Home"
                  }
               ],
               "flag_value":"Campus",
               "desc":"Campus",
               "name":"UD11_DESC"
            },
            {UD[12-19]_DESC},
            { 
               "flag_name":"UD20_DESC",
               "id":20,
               "lookups":[ 
                  { 
                     "code":"ABC",
                     "desc":"ABCD"
                  }
               ],
               "flag_value":"Alpha Code",
               "desc":"Alpha Code",
               "name":"UD20_DESC"
            },
            { 
               "flag_name":"UD21_DESC",
               "id":21,
               "flag_value":"Visa Number/Date",
               "desc":"Visa Number/Date",
               "name":"UD21_DESC"
            },
            {UD[22-24]_DESC},
            { 
               "flag_name":"UD25_DESC",
               "id":25,
               "flag_value":"Application date",
               "desc":"Application date",
               "name":"UD25_DESC"
            }
         ]
      }
    ```
 
* **Error Response:**

    `includelookups` is not supplied
    ```javascript
      "__invalid": {
        "includelookups": "field is required"
      }
    ```
    
* **Sample Parameters:**

  ```javascript
    {"includelookups":"true"}
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getStudentUDSetup&appcode=DEMOSD&company=10&v=2&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getStudentUDSetup">
       <input type="hidden" name="appcode" value="DEMOSD">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="2">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```

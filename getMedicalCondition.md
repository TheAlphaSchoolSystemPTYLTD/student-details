**getMedicalCondition**
----
  Returns a structured student medical condition details data in JSON format.
  
* **Version History:**

  TASS v52.3 - Method Added

* **Version:**

  3

* **Permission:**

  Medical Setup > Student Medical > Medical Conditions tab > View

* **Method:**

  `GET | POST`
  
*  **Params:**

   **Required:**
 
   `studcode [string]` - Student Code

   `mcond_code [string]` - Medical Condition Code

   **Optional:**

   None

   **Conditional:**

   None

* **Success Response:**

    ```javascript
      { 
         "attachment":[ 
            { 
               "attach_id_filename":"transaction.JPG",
               "mcond_code":"AST",
               "attach_id":"5F724726-E361-C720-A1160233A4E8893D"
            }
         ],
         "medication_notes":[ 
            { 
               "note_date":"2018-04-30 00:00:00.0",
               "note_text":"she has trouble breathing apparently."
            },
            { 
               "note_date":"2014-09-04 00:00:00.0",
               "note_text":"Asthma (from the Greek ?s?µa, ásthma, \"panting\") is a common chronic inflammatory disease of the airways characterized by variable and recurring symptoms..."
            },
            { 
               "note_date":"2006-03-09 00:00:00.0",
               "note_text":"Andrea needs to be reminded that she should use ventolin before an attack becomes serious."
            },
            { 
               "note_date":"2004-06-04 00:00:00.0",
               "note_text":"Andrea had another attack of Asthma, this time more serious. It was advised by her GP that she be taken straight to hospital.  Telephoned her father at work and rushed her straight to Wesley Hospital."
            },
            { 
               "note_date":"2004-06-01 00:00:00.0",
               "note_text":"Andrea had a moderate attack of Asthma and was immediately administered Ventolin by the School Nurse."
            }
         ],
         "general_note":"Andrea had signs of worsening Asthma.",
         "ud_area":{ 
            "Ventolin - Does the student xx":"Carries Ventolin with her at all times when she remembers xx",
            "Expiry date of medication":"01/03/2016",
            "Authorised staff member":"123456789012345678901234567890123456789012345678901234567890",
            "Dosage":"123456789012345678901234567890123456"
         },
         "date_of_last_occurence":"2018-12-06 00:00:00.0",
         "token":{ 
            "timestamp":"{ts '2020-02-14 09:11:17'}",
            "studcode":"0009130",
            "mcond_code":"AST"
         },
         "severe_condition":"Y",
         "medication_requirements":[ 
            { 
               "med_detl":"",
               "med_text":"Testing medication for V48",
               "med_meth":""
            },
            { 
               "med_detl":"Will usually alleviate attack but it may not.  She might still be wheezing and carrying on like a broken kettle. xxxxxxxxxxxxxxxx xxxxxxxxxxxxxx xxxxxxxxxxxxxxxxx xxxxxxxxxxxxxxxxxx xxxxxxxxxx xxxxend",
               "med_text":"Ventolin though not juts any brand it must be the GlaxoSmithKline band.  Nothing else is acceptable because the parents work for GlaxoSmithKline.  How long is this field anyway.  Ridiculously long xxx",
               "med_meth":"Uses a puffer.  Oh dear god I hope this field is not as long as the one above.  I am running out of things to say about medication.  Why would you have a field this long accessed through a small xxend"
            }
         ]
      }
    ```
 
* **Error Response:**

    `studcode` not supplied
    ```javascript
      "error": "studcode is required."
    ```

    `mcond_code` not supplied
    ```javascript
      "error": "mcond_code is required."
    ```

* **Sample Parameters:**

  ```javascript
    {"studcode":"0009130","mcond_code":"AST"}
  ```

* **Sample GET:** (With URL Encoded `token`)

  ```HTML
    http://api.tasscloud.com.au/tassweb/api/?method=getMedicalCondition&appcode=API10&company=10&v=3&token=l1D8owEn111IHcXLRwXTB0oU2GX6rj%2BISqa9zXA8We3J3mwgjW5pdUvFK3%2FIZ4mJ4bMyfKTmEoup%2B3tTE9GeLQ%3D%3D
  ```
  
* **Sample POST:**

  ```HTML
    <form id="postForm" name="postForm" method="POST" action="http://api.tasscloud.com.au/tassweb/api/">
       <input type="hidden" name="method" value="getMedicalCondition">
       <input type="hidden" name="appcode" value="API10">
       <input type="hidden" name="company" value="10">
       <input type="hidden" name="v" value="3">
       <textarea name="token">l1D8owEn111IHcXLRwXTB0oU2GX6rj+ISqa9zXA8We3J3mwgjW5pdUvFK3/IZ4mJ4bMyfKTmEoup+3tTE9GeLQ==</textarea>
    </form>
  ```
# Capstone Required Error Messages
![if-inputs-are-required-quote](https://user-images.githubusercontent.com/89945390/172217607-f8c2f8d0-6a86-40e9-9c64-5f4d737d8d60.jpg)
#### Quick note on the above point:
- Conveying meaning with color alone is *not* intuitive, especially for those with disabilites. Please check out this section of the W3 article [Designing for Web Accessibility](https://www.w3.org/WAI/tips/designing/#dont-use-color-alone-to-convey-information) to see more information on this! Especially important for letting users know what is required.
![w3 conveying meaning with color](https://user-images.githubusercontent.com/89945390/172491261-e2cdac57-aef4-49f1-9c9b-5bc37e641b5a.png)

----------------------------

## How to use this Guide:

Below we have [common input fields](https://github.com/whitnessme/capstone-minimum-required-error-messages#common-input-fields), [different datatypes](https://github.com/whitnessme/capstone-minimum-required-error-messages#different-datatypes) -- with questions relating to each that represent a validation you will possibly need--and [CSS Checks](https://github.com/whitnessme/capstone-minimum-required-error-messages#css-checks) that you'll need to implement. Keep in mind, there needs to be a *specific* error message that is displayed for the user for *EVERY* single validation. If a user can't submit something and nothing happens, you must tell them **why**! A good way to think of these are as *edge cases*! 

**DISCLAIMER:** This isn't a comprehensive list, please consider any other error messages for your specific forms/database needs!
*(example: it can't have the default "This field is required", it needs to be a clear specific sentence.)*
Some of these don’t apply to every situation, if they do apply, they are required, but those marked with an asterisk (*) are *always* required!

*^ which this is a good example of making it obvious what is required!*

> Example Error Messages:

![example error messages](https://user-images.githubusercontent.com/89945390/172720450-594cee46-98ca-4dfb-b32e-21b473ea77c2.png)

-----------------------

## Common Input Fields:

- **Email**
     - [ ] Is it a valid email?*
-  **Password**
    - [ ] Is it matching the confirm password field?*
-  **Address**
    - *If it’s only for display purposes, there doesn’t need to be separated fields*    
    -  *If in separate fields:*
        - [ ] U.S. Zip code – 5 integers*
     - [ ] If an external API is dependent on it, there might be more validations needed for each field.
-  **Cell/Phone Numbers**
    - [ ]  Length of 10 integers* (for the U.S)
- **Money**
    - [ ] Is the value negative?*
    - [ ] Is the value only 2 decimal points over? (float, `step="0.01"`)
 
----------

## Different Datatypes:

**String Errors:**

- [ ]  Is a blank entry valid? (and you can tell exactly which field its referring to)
- [ ]  Max length (error telling specifically the range/limit)*
- [ ]  Min length (when appropriate)

**Integer/Number Errors:**

- [ ] Is zero/blank a valid entry?
- [ ] Does the value only contain numbers?
- [ ] Are negative numbers valid?
- [ ] Min # (when appropriate)
- [ ] Max # (when appropriate)

**Date/Time Errors:**

- [ ] Is a blank entry valid?*
- [ ] Is today a valid entry?
- [ ] Are past dates/times valid?

**Date/Time Range Errors:**

- [ ] Start time can’t be after end time*
- [ ] Are overlapping dates valid from user to user?
- [ ] Are overlapping dates valid for a single user?

**Image/Video/Audio Errors:**

-  **URL (Images only)**
    - [ ] Is a blank entry valid?
    - [ ] Check the end of the url for valid image file types (.jpg, .png, .gif…etc)*
    - [ ] Don’t need to check if it is a valid link before submitting, but have a plan to handle broken images.*
- **External API (applies to Videos & Audio, too)**
    - [ ] Is it a valid file type? (needs to tell them specifically what extensions are valid)*
    - [ ] Is the size of the file too large? (not required but highly recommended!)

----------

## CSS Checks
> From what users could enter -- the READ of CRUD. Not planning for these can result in some buggy looking apps!

- [ ] Long string (no spaces) | Word-break & overflow*
- [ ] Max length | Word-wrap & overflow*

*Example:*

![text outside of div](https://user-images.githubusercontent.com/89945390/172492326-1341dcdb-28b1-4449-815d-ae039fd96ec1.png)

## Adrian's Capstone Slides
- [Instructor Notes on Capstone Project Grading](https://docs.google.com/presentation/d/1U3dFDQYXZbI9YTnC9T--hYtSIDobhbTU6F3lUBnSkjc/edit#slide=id.p)

----------------

## Closing Reminders:
- Remember that CREATE and UPDATE validations need to be identical. 
- Remember to change the default message format--especially if your column names are coming through with underscores, this appears buggy. *Example: "first_name: This field is required"* 
    - *For the flask starter:* The field name in front of the error message is set in `app/api/auth_routes.py`, in the first function ` validation_errors_to_error_messages`, if you wish to remove it.
- Even with optional input fields, there should be at least one or more validations for every input and it is obvious it is optional. (Very rare cases when there are none. Please reach out to us to get approval.)
- This is definitely good for recruiters to not be confused and see good attention to detail when they potentially go through your app.
- You are responsible for making sure you don't have any bugs on final grading, even if its not caught on pre-grading! Test, test, test! Go through all your user stories and check them off.

[Back to top ⤴](https://github.com/whitnessme/capstone-minimum-required-error-messages#capstone-required-error-messages)

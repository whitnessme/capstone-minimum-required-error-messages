# Capstone Required Error Messages
![if-inputs-are-required-quote](https://user-images.githubusercontent.com/89945390/172217607-f8c2f8d0-6a86-40e9-9c64-5f4d737d8d60.jpg)

----------------------------

## Table of Contents:

- [How to use this Guide](https://github.com/whitnessme/capstone-minimum-required-error-messages#how-to-use-this-guide)
- [Different Datatypes](https://github.com/whitnessme/capstone-minimum-required-error-messages#1-different-datatypes)
    - String, Integer/Num, Date/Time, & Date/Time Ranges
- [URL File Data](https://github.com/whitnessme/capstone-minimum-required-error-messages#2-url-file-data)
    - Image URL
    - External API for Image, Audio, Video
- [Common Input Fields](https://github.com/whitnessme/capstone-minimum-required-error-messages#3-common-input-fields)
- [CSS Checks](https://github.com/whitnessme/capstone-minimum-required-error-messages#4-css-checks)
- [More Important Information](https://github.com/whitnessme/capstone-minimum-required-error-messages#5-more-important-information)
    - [Keep in Mind](https://github.com/whitnessme/capstone-minimum-required-error-messages#keep-in-mind)
    - [Capstone Grading Slides](https://github.com/whitnessme/capstone-minimum-required-error-messages#capstone-grading-slides)
- [Bonus Information](https://github.com/whitnessme/capstone-minimum-required-error-messages#6-bonus-information)
    - [Accessibility](https://github.com/whitnessme/capstone-minimum-required-error-messages#accessibility)
    - [Extra Validations not required for passing](https://github.com/whitnessme/capstone-minimum-required-error-messages#extra-validations-not-required-for-passing)

------------
## How to use this Guide:

Below we have [Different Datatypes](https://github.com/whitnessme/capstone-minimum-required-error-messages#1-different-datatypes), [Common Input Fields](https://github.com/whitnessme/capstone-minimum-required-error-messages#2-common-input-fields), [URL File Data](https://github.com/whitnessme/capstone-minimum-required-error-messages#2-url-file-data) with questions relating to each that represent a validation you will possibly need. **If the answer to the question is "YES" or the line has an asterisk (*) then you need a validation & error message for that point!**
Keep in mind, there needs to be a *specific* error message that is displayed for the user for *EVERY* single validation.
#### If a user can't submit something and nothing happens, you must tell them **why**! A good way to think of these are as *edge cases*! 
After those, we have [CSS Checks](https://github.com/whitnessme/capstone-minimum-required-error-messages#3-css-checks) for things you'll need to implement to make sure user inputted data displays properly.

**DISCLAIMER:** This isn't a comprehensive list, please consider any other error messages for your specific forms/database needs!
Some of these don’t apply to every situation. If they do apply, *they are required*, and those marked with an asterisk (*) are *always* required!

> Example Error Messages:

![error messages example](https://user-images.githubusercontent.com/89945390/190253731-7a768b73-ed0e-473a-9980-330128eb4167.png)

-----------------------

## 1. Different Datatypes:
![date range error example](https://user-images.githubusercontent.com/89945390/190273095-5b311f5e-abf3-43a7-b25d-30e065c50695.png)

**String Errors:**

- [ ]  Is data required?
- [ ]  Does the value excede the max length?* (There should be always be a max length set with the error message or instructions telling the specific range/limit)
- [ ]  Is there a minimum length?
- [ ] Are unique entries required?

**Integer/Number Errors:**

- [ ] Does the value only contain numbers?*
- [ ] Is zero not valid?
- [ ] Is data required?
- [ ] Are negative numbers not valid?
- [ ] Does the value fail to reach the minimum limit?
- [ ] Does the value excede the maximum limit?

**Date/Time Errors:**

- [ ] Is data required?
- [ ] Is today not a valid entry?
- [ ] Are past dates/times not valid?
- [ ] Is the same date/time not valid if another user already reserved it?
    - *Example:* a user can't get an appointment with a realtor if another user already booked with them at that time. 
- [ ] Is the same date/time not valid if the user themselves already reserved elsewhere?
    - *Example:* a user can't get a second appointment with a realtor if they already have an appoitment with someone else at the same time. 

**Date/Time Range Errors:**

- [ ] Is the start time after the end time?*
- [ ] Are overlapping dates/time ranges not valid if another user already reserved them?
    - *Example:* Users can't book the same Airbnb when someone else has those days booked.
- [ ] Are overlapping dates/time ranges not valid if the user themselves already reserved elsewhere?

-------------------
## 2. URL File Data

**Image Errors for User-inputted URL**
- [ ] Is data required?
- [ ] Check the beginning of the url for "http://" or "https://"* (with error message telling them it's needed)
- [ ] Check the end of the url for valid image file types* (with error message telling what valid types are: .jpg, .png, .gif, etc...)
- [ ] You don’t need to check if it is a valid image/link before the user submits, but have a plan to handle broken images.*
    - This can be done by using the `onError` property (Go to MDN and look at the ["Image loading errors" section of the <img> element page](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img#image_loading_errors) to better understand what is going on.)
    ```
    <img 
        src={original.image} 
        alt="image description for screen readers"
        onError={e => { e.currentTarget.src = "your_image_not_found_defalt_picture_here"; }}
   />
   ```
	
**Image/Video/Audio External API Errors (like AWS)**
- [ ] Is it not a valid file type?* (error message needs to tell specifically what extensions are valid)
    - Do not make the mistake of thinking limiting what type of file the "Browse..." button will open will allow you to not have this validation, users can still drag files onto that field. To test this, drag a .txt or some other file type onto the "Browse..." input field.

----------

## 3. Common Input Fields:

![email and password error message examples](https://user-images.githubusercontent.com/89945390/190252956-cec49be0-06f4-4b6b-9592-cd1deb1665a2.png)

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

----------------

## 4. Data Persistence:
### Think of the User Experience:
- CREATE and EDIT forms should have User inputs persisting if the form failed to submit.
    - If a constraint is not met for a field in a form, it would be inconvenient if all other inputs are lost/reset.
    	- An example would be a user losing all the inputs made for a Review body after pressing submit, if a required Star Rating was forgotten.
    - Multi-step/page forms should have the data on their fields persist even after switching to a different step/page on the form.
        - Consider the most likely case that a User needs to go back and change an input field from a previous step.
- EDIT forms should pre-populate the form fields with what is currently saved on the Database for that entry. 
    - A common example where this is essential is when a User decides to fix a typo from a previously submitted Posts.
### Consider Data Security as well (Soft Requirement but ideal):
- Avoid persisting sensitive data such as passwords, credit card info, etc...
    - Consider either hiding or encrypting the data for such fields.
 
----------

## 5. CSS Checks
> From what users could enter -- the READ of CRUD. [Not planning for these can result in some buggy looking apps!](https://docs.google.com/presentation/d/1U3dFDQYXZbI9YTnC9T--hYtSIDobhbTU6F3lUBnSkjc/edit#slide=id.g11627660d89_0_20)

- [ ] Long string (no spaces) | Word-break & overflow*
- [ ] Max length | Word-wrap & overflow*

> Example of text going outside div:

![text outside of div](https://user-images.githubusercontent.com/89945390/172492326-1341dcdb-28b1-4449-815d-ae039fd96ec1.png)

----------------

## 6. More Important Information
### Keep in Mind:
- CREATE and UPDATE validations need to be identical. 
- Change the default message format--especially if your column names are coming through with underscores, this appears buggy. *Example: "first_name: This field is required"* 
    - *For the flask starter:* The field name in front of the error message is set in `app/api/auth_routes.py`, in the first function ` validation_errors_to_error_messages`, if you wish to remove it.
- Even if data isn't required on an input field, there should be at least one validation for every input. (Very rare cases when there are none. Please reach out to us to get approval.)
- Error handling and letting users know what to do make your apps actually usable & navigatable. **You are responsible for making sure you don't have any bugs on final grading, even if its not caught on pre-grading!** Go through all your user stories and check them off.

-------------------

## 7. Bonus Information
### Accessibility:
- Conveying meaning with color alone is *not* intuitive, especially for those with disabilites. Please check out this section of the W3 article [Designing for Web Accessibility](https://www.w3.org/WAI/tips/designing/#dont-use-color-alone-to-convey-information) to see more information on this! Especially important for letting users know what is required.
![w3 conveying meaning with color](https://user-images.githubusercontent.com/89945390/172491261-e2cdac57-aef4-49f1-9c9b-5bc37e641b5a.png)

### Extra Validations not required for passing
- [ ] Prevent users from submiting only white-space** *(example: `"           "`)* *.
        - This is easily handled by [trimming](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/trim) the input data and checking if the length is 0.
- [ ] Prevent users from uploading large files to your AWS bucket. 

[Back to top ⤴](https://github.com/whitnessme/capstone-minimum-required-error-messages#capstone-required-error-messages)

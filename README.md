# Capstone Required Error Messages
![if-inputs-are-required-quote](https://user-images.githubusercontent.com/89945390/172217607-f8c2f8d0-6a86-40e9-9c64-5f4d737d8d60.jpg)

----------------------------

## Table of Contents:

1. [Different Datatypes](https://github.com/whitnessme/capstone-minimum-required-error-messages#1-different-datatypes)
2. [Common Input Fields](https://github.com/whitnessme/capstone-minimum-required-error-messages#2-common-input-fields)
3. [CSS Checks](https://github.com/whitnessme/capstone-minimum-required-error-messages#3-css-checks)
4. [More Important Information](https://github.com/whitnessme/capstone-minimum-required-error-messages#4-more-important-information)
    - [Keep in Mind](https://github.com/whitnessme/capstone-minimum-required-error-messages#keep-in-mind)
    - [Do my forms need labels?](https://github.com/whitnessme/capstone-minimum-required-error-messages#do-my-forms-need-labels)
    - [Capstone Grading Slides](https://github.com/whitnessme/capstone-minimum-required-error-messages#capstone-grading-slides)
5. [Bonus Information](https://github.com/whitnessme/capstone-minimum-required-error-messages#bonus-information)
    - [Accessibility](https://github.com/whitnessme/capstone-minimum-required-error-messages#accessibility)

------------
## How to use this Guide:

Below we have [Different Datatypes](https://github.com/whitnessme/capstone-minimum-required-error-messages#1-different-datatypes), [Common Input Fields](https://github.com/whitnessme/capstone-minimum-required-error-messages#2-common-input-fields) -- with questions relating to each that represent a validation you will possibly need--and [CSS Checks](https://github.com/whitnessme/capstone-minimum-required-error-messages#3-css-checks) that you'll need to implement. Keep in mind, there needs to be a *specific* error message that is displayed for the user for *EVERY* single validation.
#### If a user can't submit something and nothing happens, you must tell them **why**! A good way to think of these are as *edge cases*! 

**DISCLAIMER:** This isn't a comprehensive list, please consider any other error messages for your specific forms/database needs!
Some of these don’t apply to every situation, if they do apply, they are required, but those marked with an asterisk (*) are *always* required!

> Example Error Messages:

![error messages example](https://user-images.githubusercontent.com/89945390/190253731-7a768b73-ed0e-473a-9980-330128eb4167.png)

-----------------------

## 1. Different Datatypes:

**String Errors:**

- [ ]  Is data required?*
    - [ ] If yes, you need to **prevent users from submiting only white-space** (like spaces)*.
        - This is easily handled by [trimming](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/trim) the input data and checking if the length is 0.
- [ ]  Max length (error telling specifically the range/limit)*
- [ ]  Min length (when appropriate)

**Integer/Number Errors:**

- [ ] Is zero valid?
- [ ] Is data required?*?
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
    - [ ] You don’t need to check if it is a valid link before submitting, but have a plan to handle broken images.*
        - This can be done by using the `onError` property (Go to MDN and look at the ["Image loading errors" section of the <img> element page](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img#image_loading_errors) to better understand what is going on.)
        ```
          <img 
	          src={original.image} 
               alt=""
               onError={e => { e.currentTarget.src = "your_image_not_found_defalt_picture_here"; }}
          />
        ```
- **External API (applies to Videos & Audio, too)**
    - [ ] Is it a valid file type? (needs to tell them specifically what extensions are valid)*
    - [ ] Is the size of the file too large? (not required but highly recommended!)

----------

## 2. Common Input Fields:

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
 
----------

## 3. CSS Checks
> From what users could enter -- the READ of CRUD. [Not planning for these can result in some buggy looking apps!](https://docs.google.com/presentation/d/1U3dFDQYXZbI9YTnC9T--hYtSIDobhbTU6F3lUBnSkjc/edit#slide=id.g11627660d89_0_20)

- [ ] Long string (no spaces) | Word-break & overflow*
- [ ] Max length | Word-wrap & overflow*

> Example of text going outside div:

![text outside of div](https://user-images.githubusercontent.com/89945390/172492326-1341dcdb-28b1-4449-815d-ae039fd96ec1.png)

----------------

## 4. More Important Information
### Keep in Mind:
- CREATE and UPDATE validations need to be identical. 
- Change the default message format--especially if your column names are coming through with underscores, this appears buggy. *Example: "first_name: This field is required"* 
    - *For the flask starter:* The field name in front of the error message is set in `app/api/auth_routes.py`, in the first function ` validation_errors_to_error_messages`, if you wish to remove it.
- Even if data isn't required on an input field, there should be at least one validation for every input. (Very rare cases when there are none. Please reach out to us to get approval.)
- Error handling and letting users know what to do make your apps actually usable & navigatable. **You are responsible for making sure you don't have any bugs on final grading, even if its not caught on pre-grading!** Go through all your user stories and check them off.

### Do my forms need labels?
- 

### Capstone Grading Slides
> Please check out this file for more in depth information.
- [Instructor Notes on Capstone Project Grading](https://docs.google.com/presentation/d/1U3dFDQYXZbI9YTnC9T--hYtSIDobhbTU6F3lUBnSkjc/edit#slide=id.p)

-------------------

## 5. Bonus Information
### Accessibility:
- Conveying meaning with color alone is *not* intuitive, especially for those with disabilites. Please check out this section of the W3 article [Designing for Web Accessibility](https://www.w3.org/WAI/tips/designing/#dont-use-color-alone-to-convey-information) to see more information on this! Especially important for letting users know what is required.
![w3 conveying meaning with color](https://user-images.githubusercontent.com/89945390/172491261-e2cdac57-aef4-49f1-9c9b-5bc37e641b5a.png)

[Back to top ⤴](https://github.com/whitnessme/capstone-minimum-required-error-messages#capstone-required-error-messages)

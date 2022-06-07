# Capstone Required Error Messages
![if-inputs-are-required-quote](https://user-images.githubusercontent.com/89945390/172217607-f8c2f8d0-6a86-40e9-9c64-5f4d737d8d60.jpg)
#### Quick note on the above point:
- Conveying meaning with color alone is *not* intuitive, especially for those with disabilites. Please check out this section of the W3 article [Designing for Web Accessibility](https://www.w3.org/WAI/tips/designing/#dont-use-color-alone-to-convey-information) to see more information on this! Especially important for letting users know what is required.
![w3 conveying meaning with color](https://user-images.githubusercontent.com/89945390/172491261-e2cdac57-aef4-49f1-9c9b-5bc37e641b5a.png)

## How to use this Guide:

Below we have common input fields and different datatypes and questions relating to each that represent a validation you will possibly need. Keep in mind, there needs to be a *specific* error message that is displayed for the user for *EVERY* single validation. If a user can't submit something and nothing happens, you must tell them **why**!

**DISCLAIMER:** This isn't a comprehensive list, please consider any other error messages for your specific forms/database needs! 
Some of these don’t apply to every situation, if they do apply, they are required, but those marked with an asterisk (*) are *always* required!

*^ which this is a good example of making it obvious what is required!*

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
 
----------

## Different Datatypes:

**String Errors:**

- [ ]  Is a blank entry valid? (and you can tell exactly which field its referring to)*
- [ ]  Max length (error telling specifically the range/limit)*
- [ ]  Min length (when appropriate)

**Integer/Number Errors:**

- [ ] Is zero/blank a valid entry?*
- [ ] Are negative numbers valid?*
- [ ] Min # (when appropriate)
- [ ] Max # (when appropriate)

**Date/Time Errors:**

- [ ] Is a blank entry valid?*
- [ ] Is today a valid entry?*
- [ ] Are past dates/times valid?*

**Date/Time Range Errors:**

- [ ]  Start time can’t be after end time*
- [ ] Are overlapping dates valid from user to user?
- [ ] Are overlapping dates valid for a single user?

**Image/Video/Audio Errors:**

-  **URL (Images only)**
    - [ ] Is a blank entry valid?*
    - [ ] Check the end of the url for valid image file types (.jpg, .png, .gif…etc)*
    - [ ] Don’t need to check if it is a valid link before submitting, but have a plan to handle broken images.*
- **External API (applies to Videos & Audio, too)**
    - [ ] Is it a valid file type? (needs to tell them specifically what extensions are valid)*
    - [ ] Is the size of the file too large? (highly recommended!)

----------

## CSS Checks
> From what users could enter -- the READ of CRUD. 

- [ ] Long string (no spaces) | Word-break & overflow
- [ ] Max length | Word-wrap & overflow

## Adrian's Capstone Slides
- [Instructor Notes on Capstone Project Grading](https://docs.google.com/presentation/d/1U3dFDQYXZbI9YTnC9T--hYtSIDobhbTU6F3lUBnSkjc/edit#slide=id.p)

----------------

[Back to top ⤴](https://github.com/whitnessme/capstone-minimum-required-error-messages#capstone-required-error-messages)

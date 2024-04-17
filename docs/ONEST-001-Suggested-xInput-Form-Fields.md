# Suggested Form Structure for xInput

When the Provider app sends a form to the Seeker app to get further details from the user, they can use the following `name` attributes in their `input` tags or `select` tags in their `form`. The seeker app may use this to auto fill the values from user profiles at their end.

| Name Attribute             | HTML Tag       | Description                                                  | Allowed Values                | Remarks                                                                 |
| -------------------------- | -------------- | ------------------------------------------------------------ | ----------------------------- | ----------------------------------------------------------------------- |
| user-full-name             | input text     | Full Name                                                    |                               | To be returned in `customer.person.name` in subsequent calls.           |
| user-first-name             | input text     | First Name                                                    |                               | First name, middle name and last name to be concatenated and returned in customer.person.name in subsequent calls          |
| user-middle-name             | input text     | Middle Name                                                    |                               | First name, middle name and last name to be concatenated and returned in customer.person.name in subsequent calls               |
| user-last-name             | input text     | Last Name                                                    |                               | First name, middle name and last name to be concatenated and returned in customer.person.name in subsequent calls        |
| user-date-of-birth         | input text     | Date of Birth                                                |                               | To be returned in `customer.person.dob` in subsequent calls.            |
| user-gender                | select     | Gender                                                       | Male, Female, Transgender, Other | To be returned in `customer.person.gender` in subsequent calls.      |
| user-email                 | input text     | Email                                                        |                               | To be returned in `customer.contact.email` in subsequent calls.         |
| user-phone-number          | input text     | Phone number                                                 |                               | To be returned in `customer.contact.phone` in subsequent calls.         |
| user-bank-ifsc             | input text     | IFSC of the bank                                             |                               | To be returned in `payent.params.bank_code` in subsequent calls.        |
| user-bank-acc-no           | input text     | Bank account number                                          |                               | To be returned in `payent.params.bank_account_number` in subsequent calls.|
| user-bank-acc-name         | input text     | Beneficiary name of the bank account                         |                               | To be returned in `payent.params.bank_account_name` in subsequent calls.|
| user-bank-name         | input text     | Name of the bank  |                               | |
| user-bank-acc-statement        | input text     | Bank Account Statement |                               | |
| user-social-category       | select         | User's social category                                       |                               |                                                                         |
| user-occupation            | select         | User's occupation                                            | Refer to occupations section. |                                                                         |
| user-phone-verified        | input checkbox | Whether the phone number provided by the seeker is verified  |                               |                                                                         |
| user-email-verified        | input checkbox | Whether the email address provided by the seeker is verified |                               |                                                                         |
| user-bank-details-verified | input checkbox | Whether the bank details provided by the seeker is verified  |                               |                                                                         |
| user-guardian-full-name      | input text     | User's guardian's full name                                    |                               |                                                                         |
| user-guardian-occupation     | select         | User's guardian's occupation                                   |                               |                                                                         |
| user-guardian-phone          | input text     | User's guardian's phone number                                 |                               |                                                                         |
| user-ann-hh-inc            | input text     | User's annual household income                               |                               |                                                                         |
| user-address               | input text     | Address of the user                                          |                               | This can be returned in `billing.address` in subsequent calls           |
| \<Document Name/ID>-verified  | input checkbox | Whether the document is verified by the agent                |                               | Please see the list of documents to see the values \<Document Name> can take |
| \<Document Name/ID>-doc       | input file     | Document as pdf or image                                     |                               | Please see the list of documents to see the values \<Document Name> can take |
| <edu-qual-level>-qual-name | input file | Name of the course |  | Please see the list of education qualification table below to see the values \<edu-qual-level> can take |
| <edu-qual-level/edu-qual-name>-status | select | Status of the course | "Registered", "In-Progress", "Completed", "Dropped" |  | Please see the list of education qualification table below to see the values \<edu-qual-level/edu-qual-name> can take  |
| <edu-qual-level/edu-qual-name>-issued-by | input file | University or board that issued the course certificate |  | Please see the list of education qualification table below to see the values \<edu-qual-level/edu-qual-name> can take |
| <edu-qual-level/edu-qual-name>-score-obtained | input text | Score obtained by the user for the qualification/course |  | Please see the list of education qualification table below to see the values \<edu-qual-level/edu-qual-name> can take |
| <edu-qual-level/edu-qual-name>-score-total | input text | Maximum score possible for the qualification/course and should be entered including total possible score. Example: 8.7/10, 4.5/5, B+/A+, 560/600. |  | Please see the list of education qualification table below to see the values \<edu-qual-level/edu-qual-name> can take |
| <edu-qual-level/edu-qual-name>-percentage | input text | Percentage score obtained by the student for the qualification/course |  | Please see the list of education qualification table below to see the values \<edu-qual-level/edu-qual-name> can take |
| <edu-qual-level/edu-qual-name>-completion-month | input text | Completion Month and Year for the qualification/course |  | Please see the list of education qualification table below to see the values \<edu-qual-level/edu-qual-name> can take |
| <edu-qual-level/edu-qual-name>-institution-name | input text | Name of the Institution |  | Please see the list of education qualification table below to see the values \<edu-qual-level/edu-qual-name> can take |
| <edu-qual-level/edu-qual-name>-institution-state | input text | State in which institution is located. |  | Please see the list of education qualification table below to see the values \<edu-qual-level/edu-qual-name> can take |
| <edu-qual-level/edu-qual-name>-subject | input text | Subjects or specializations covered as part of a education qualification |  | Please see the list of education qualification table below to see the values \<edu-qual-level/edu-qual-name> can take |
| <edu-qual-level/edu-qual-name>-id-card | file | Photo of ID Card |  | Please see the list of education qualification table below to see the values \<edu-qual-level/edu-qual-name> can take |
| edu-qual-level-<n> | input text | Qualification level of the user |  | <n> is an integer where 0 means current. If user is not currently enrolled then 0 means latest. 1 means the one before that and so on.  |
| edu-qual-name-<n> | input text | Name of the course/qualification |  | <n> is an integer where 0 means current. If user is not currently enrolled then 0 means latest. 1 means the one before that and so on.  |
| edu-qual-status-<n> | select | Status of the course/qualification | "Registered", "In-Progress", "Completed", "Dropped" | <n> is an integer where 0 means current. If user is not currently enrolled then 0 means latest. 1 means the one before that and so on.  |
| edu-qual-issued-by-<n> | input file | University or board that issued the course certificate |  | <n> is an integer where 0 means current. If user is not currently enrolled then 0 means latest. 1 means the one before that and so on.  |
| edu-qual-score-obtained-<n> | input file | Score obtained by the user for the qualification/course. |  | <n> is an integer where 0 means current. If user is not currently enrolled then 0 means latest. 1 means the one before that and so on.  |
| edu-qual-score-total-<n> | input file | Maximum score possible for the qualification/course and should be entered including total possible score. Example: 8.7/10, 4.5/5, B+/A+, 560/600. |  | <n> is an integer where 0 means current. If user is not currently enrolled then 0 means latest. 1 means the one before that and so on.  |
| edu-qual-percentage-<n> | input file | Percentage score obtained by the student for a education qualification |  | <n> is an integer where 0 means current. If user is not currently enrolled then 0 means latest. 1 means the one before that and so on.  |
| edu-qual-completion-month-<n> | input text | Course Completion Month and Year |  | <n> is an integer where 0 means current. If user is not currently enrolled then 0 means latest. 1 means the one before that and so on.  |
| edu-qual-institution-name-<n> | input text | Name of the Institution |  | <n> is an integer where 0 means current. If user is not currently enrolled then 0 means latest. 1 means the one before that and so on.  |
| edu-qual-institution-state-<n> | input text | State in which institution is located. | ISO_3166-2:IN state code |  | <n> is an integer where 0 means current. If user is not currently enrolled then 0 means latest. 1 means the one before that and so on.  |
| edu-qual-subject-<n> | input text | Subjects or specializations covered as part of a education qualification |  | <n> is an integer where 0 means current. If user is not currently enrolled then 0 means latest. 1 means the one before that and so on.  |
| edu-qual-id-card-<n> | file | Photo of ID Card | | <n> is an integer where 0 means current. If user is not currently enrolled then 0 means latest. 1 means the one before that and so on.  |

### List of documents

| Document                     | Document Name               | Allowed IDs     | Document ID                 | Description                                                                                                    |
| ---------------------------- | --------------------------- | --------------- | --------------------------- | -------------------------------------------------------------------------------------------------------------- |
| Applicant Photo              | applicant-photo             | Photo           | person-photo                | Latest photo uploaded in the seeker app                                                                        |
| Proof of Identity            | proof-of-identity           | Voter Id        | voter-id                    | PDF of Vote ID                                                                                                 |
| Proof of Identity            | proof-of-identity           | Aadhaar Card    | aadhaar-card                | digital copy of Aadhaar generated by digilocker or PDF of Aadhaar                                              |
| Proof of Identity            | proof-of-identity           | Driving License | driving-license             | e-Copy version as Image or PDF                                                                                 |
| Proof of Identity            | proof-of-identity           | Passport        | passport                    | PDF copy of the passport                                                                                       |
| Proof of Address             | proof-of-address            | Voter Id        | voter-id                    | PDF of Vote ID                                                                                                 |
| Proof of Address             | proof-of-address            | Aadhaar Card    | aadhaar-card                | digital copy of Aadhaar generated by digilocker or PDF of Aadhaar                                              |
| Proof of Address             | proof-of-address            | Driving License | driving-license             | e-Copy version as Image or PDF                                                                                 |
| Proof of Address             | proof-of-address            | Passport        | passport                    | PDF copy of the passport                                                                                       |
| 10th Mark Sheet              | class-10-marksheet          |                 | class-10-marksheet          | Document issued by State Board, CBSE, ICSE and other school boards                                             |
| 12th Mark Sheet              | class-12-marksheet          |                 | class-12-marksheet          | Document issued by School Board or Universities                                                                |
| Under Graduation Certificate | undergraduation-certificate |                 | undergraduation-certificate | Document issued by University - Final Degree certificate, Provisional degree certificate, Cumulative marksheet |
| Graduation Certificate       | graduation-certificate      |                 | graduation-certificate      | Document issued by University - Final Degree certificate, Provisional degree certificate, Cumulative marksheet |
| Professional Certificate     | professional-certificate   |                 | professional-certificate   | Experience Certificate                                                                                         |
| Resume                       | resume                      |                 | resume                      | Latest document of professional experience                                                                     |
| Income Proof                 | income-proof                |                 | income-proof                | Proof of income or Last filled ITR or Salary slips                                                                                                |
| Enrollment Receipt                | enrollment-receipt              |                 | enrollment-receipt              | Institution enrollment receipt                                                                                              |

Provider can request either a document ID or a document Name in the form. For example if the provider wants any proof of address, they will send the attribute as `proof-of-address-doc` for the file input tag in the form. The seeker can choose any proof of address document it has with them. If the provider specifically wants voter ID, then they wll send the attribute as `voter-id-doc` 

### List of Education Qualifications

| Educational Qualification Level | edu-qual-level | Educational Qualification Name | edu-qual-name |
| -------------------------------- | ------------- | ------------------------------ | ------------- |
| Primary Education | primary | Class-1 | class-1 |
| Primary Education | primary | Class-1 | class-1 |
| Primary Education | primary | Class-2 | class-2 |
| Primary Education | primary | Class-3 | class-3 |
| Primary Education | primary | Class-4 | class-4 |
| Primary Education | primary | Class-5 | class-5 |
| Secondary Education | secondary | Class-6 | class-6 |
| Secondary Education | secondary | Class-7 | class-7 |
| Secondary Education | secondary | Class-8 | class-8 |
| Secondary Education | secondary | Class-9 | class-9 |
| Secondary Education | secondary | Class-10 | class-10 |
| Higher Secondary | higher-secondary | Class-11 | class-11 |
| Higher Secondary | higher-secondary | Class-12 | class-12 |
| Undergraduate | undergraduate | Bachelors of Technology | b-tech |
| Graduate | graduate | Master of Technology | m-tech |
| Post graduate | post-graduate | PhD | phd |


### Example:

Consider the BPP wants to get the following details from the user via form
- Parent's full name
- Parent's phone number
- Gender of the user
- Following documents:
    - 10th marksheet
    - Proof of identity (driving license or passport)
    - Aadhar card

Apart from the above the BPP also want to get confirmation that the agent at the BAP end has verified these certificates. The form for the same will be as below:

```
<form action="https://bpp.com/form/1293821" method="post">

    <div>
        <label for="user-parent-full-name">Full Name of parent*</label>
        <input type="text" id="user-parent-full-name" name="user-parent-full-name" pattern="[a-zA-Z\s.]+" required />
    </div>

    <div>
        <label for="user-parent-phone">Parent's mobile Number*</label>
        <input type="text" id="user-parent-phone" name="user-parent-phone" autocomplete="off" pattern="[6-9][0-9]{9}"
            maxlength="10" required />
    </div>

    <div>
        <span>Gender*</span>
        <input type="radio" name="user-gender" id="gender1" value="Male" required /> Male
        <input type="radio" name="user-gender" id="gender2" value="Female" required /> Female
        <input type="radio" name="user-gender" id="gender3" value="Transgender" required />Transgender
        <input type="radio" name="user-gender" id="gender4" value="Other" required /> Other
    </div>

    <h3>Upload Documents</h3>

    <span><i>Note: Total documents upload size is allowed upto {upload limit set by BPP} MB and document extensions are
            allowed are '.jpg,.jpeg,.png,.pdf'</i></span><br /><br />

     <div>
        <label for="class-10-pass-year">Class 10 Pass Year*</label>
        <input type="text" id="class-10-pass-year" name="class-10-pass-year" autocomplete="off" required />
    </div>        

    <div>
        <label for="class-10-issued-by">Class 10 Certificate Issue By*</label>
        <input type="text" id="class-10-issued-by" name="class-10-issued-by" autocomplete="off" required />
    </div> 

    <div>
        <label for="graduate-edu-qual-name">Name of the graduate degree*</label>
        <input type="text" id="graduate-edu-qual-name" name="graduate-edu-qual-name" autocomplete="off" required />
    </div>   

    <div>
        <label for="proof-of-identity-doc">Proof of Identity*</label>
        <input type="file" id="proof-of-identity-doc" name="proof-of-identity-doc" accept=".jpg,.jpeg,.png,.pdf"
            required />
        <span><i>(Accepts driving license or passport)</i></span><br />
        <input type="checkbox" id="proof-of-identity-verified" name="proof-of-identity-verified" />
        <span><i>Proof of identity has been verified by the agent</i></span><br /><br />
    </div>  

    <div>
        <label for="proof-of-identity-doc">Proof of Identity*</label>
        <input type="file" id="proof-of-identity-doc" name="proof-of-identity-doc" accept=".jpg,.jpeg,.png,.pdf"
            required />
        <span><i>(Accepts driving license or passport)</i></span><br />
        <input type="checkbox" id="proof-of-identity-verified" name="proof-of-identity-verified" />
        <span><i>Proof of identity has been verified by the agent</i></span><br /><br />
    </div>

    <div>
        <label for="aadhaar-card-doc">Aadhar card*</label>
        <input type="file" id="aadhaar-card-doc" name="aadhaar-card-doc" accept=".jpg,.jpeg,.png,.pdf" required />
        <span><i>(Aadhar card image)</i></span><br /><br />
        <input type="checkbox" id="aadhaar-card-verified" name="aadhaar-card-verified" />
        <span><i>Aadhar card has been verified by the agent</i></span><br /><br />
    </div>

</form>
```





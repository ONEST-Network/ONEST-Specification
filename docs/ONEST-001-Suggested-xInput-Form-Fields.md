# Suggested Form Structure for xInput

When the Provider app sends a form to the Seeker app to get further details from the user, they can use the following `name` attributes in their `input` tags or `select` tags in their `form`. The seeker app may use this to auto fill the values from user profiles at their end.

| Name Attribute             | HTML Tag       | Description                                                  | Allowed Values                | Remarks                                                                 |
| -------------------------- | -------------- | ------------------------------------------------------------ | ----------------------------- | ----------------------------------------------------------------------- |
| user-full-name             | input text     | Full Name                                                    |                               | To be returned in `customer.person.name` in subsequent calls.           |
| user-date-of-birth         | input text     | Date of Birth                                                |                               | To be returned in `customer.person.dob` in subsequent calls.            |
| user-gender                | input text     | Gender                                                       | Male, Female, Transgender, Other | To be returned in `customer.person.gender` in subsequent calls.      |
| user-email                 | input text     | Email                                                        |                               | To be returned in `customer.contact.email` in subsequent calls.         |
| user-phone-number          | input text     | Phone number                                                 |                               | To be returned in `customer.contact.phone` in subsequent calls.         |
| user-bank-ifsc             | input text     | IFSC of the bank                                             |                               | To be returned in `payent.params.bank_code` in subsequent calls.        |
| user-bank-acc-no           | input text     | Bank account number                                          |                               | To be returned in `payent.params.bank_account_number` in subsequent calls.|
| user-bank-acc-name         | input text     | Beneficiary name of the bank account                         |                               | To be returned in `payent.params.bank_account_name` in subsequent calls.|
| user-social-category       | select         | User's social category                                       |                               |                                                                         |
| user-occupation            | select         | User's occupation                                            | Refer to occupations section. |                                                                         |
| user-phone-verified        | input checkbox | Whether the phone number provided by the seeker is verified  |                               |                                                                         |
| user-email-verified        | input checkbox | Whether the email address provided by the seeker is verified |                               |                                                                         |
| user-bank-details-verified | input checkbox | Whether the bank details provided by the seeker is verified  |                               |                                                                         |
| user-parent-full-name      | input text     | User's parent's full name                                    |                               |                                                                         |
| user-parent-occupation     | select         | User's parent's occupation                                   |                               |                                                                         |
| user-parent-phone          | input text     | User's parent's phone number                                 |                               |                                                                         |
| user-ann-hh-inc            | input text     | User's annual household income                               |                               |                                                                         |
| user-address               | input text     | Address of the user                                          |                               | This can be returned in `billing.address` in subsequent calls           |
| \<Document Name/ID>-verified  | input checkbox | Whether the document is verified by the agent                |                               | Please see the list of documents to see the values \<Document Name> can take |
| \<Document Name/ID>-doc       | input file     | Document as pdf or image                                     |                               | Please see the list of documents to see the values \<Document Name> can take |

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
| Income Proof                 | income-proof                |                 | income-proof                | Last filled ITR                                                                                                |

Provider can request either a document ID or a document Name in the form. For example if the provider wants any proof of address, they will send the attribute as `proof-of-address-doc` for the file input tag in the form. The seeker can choose any proof of address document it has with them. If the provider specifically wants voter ID, then they wll send the attribute as `voter-id-doc` 

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
        <label for="class-10-marksheet-doc">10th Marksheet*</label>
        <input type="file" id="class-10-marksheet-doc" name="class-10-marksheet-doc" accept=".jpg,.jpeg,.png,.pdf"
            required /><br />
        <span><i>(Issued by respective board, name of student match with name in the registration form and proof of
                identity)</i></span><br />
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

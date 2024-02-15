# Tags

The TagGroup schema in beckn defines a key-value set that can be listed under a common heading. The schema of the same is shown below:

```
components:
  schemas:
    TagGroup:
      description: 'A collection of tag objects with group level attributes.'
      type: object
      properties:
        display:
          description: 'Indicates the display properties of the tag group. If display is set to false, then the group will not be displayed. If it is set to true, it should be displayed. However, group-level display properties can be overriden by individual tag-level display property. As this schema is purely for catalog display purposes, it is not recommended to send this value during search.'
          type: boolean
          default: true
        descriptor:
          description: 'Description of the TagGroup, can be used to store detailed information.'
          allOf:
            - $ref: '#/components/schemas/Descriptor'
        list:
          description: 'An array of Tag objects listed under this group. This property can be set by BAPs during search to narrow the `search` and achieve more relevant results. When received during `on_search`, BAPs must render this list under the heading described by the `name` property of this schema.'
          type: array
          items:
            $ref: '#/components/schemas/Tag'
    Tag:
      description: 'Describes a tag. This is used to contain extended metadata. This object can be added as a property to any schema to describe extended attributes. For BAPs, tags can be sent during search to optimize and filter search results. BPPs can use tags to index their catalog to allow better search functionality. Tags are sent by the BPP as part of the catalog response in the `on_search` callback. Tags are also meant for display purposes. Upon receiving a tag, BAPs are meant to render them as name-value pairs. This is particularly useful when rendering tabular information about a product or service.'
      type: object
      properties:
        descriptor:
          description: 'Description of the Tag, can be used to store detailed information.'
          allOf:
            - $ref: '#/components/schemas/Descriptor'
        value:
          description: The value of the tag. This set by the BPP and rendered as-is by the BAP.
          type: string
        display:
          description: 'This value indicates if the tag is intended for display purposes. If set to `true`, then this tag must be displayed. If it is set to `false`, it should not be displayed. This value can override the group display value.'
          type: boolean
    Descriptor:
      description: Physical description of something.
      type: object
      properties:
        name:
          type: string
        code:
          type: string
        short_desc:
          type: string
        long_desc:
          type: string
        additional_desc:
          type: object
          properties:
            url:
              type: string
            content_type:
              type: string
              enum:
                - text/plain
                - text/html
                - application/json
```

They are used to transmit additional information that is not supported in the underlying schema. In financial support domain various eligibility criteria and details regarding the application process can be represented using tag groups.

| Name (groups/\[index]/descriptor.name) | Code groups/\[index]/descriptor.code | Description                                                                               |
| -------------------------------------- | ------------------------------------ | ----------------------------------------------------------------------------------------- |
| Background eligibility                 | background-eligibility               | Eligibility criteria based on demographic details of the candidate                        |
| Academic eligibility                   | academic-eligibility                 | Eligibility based academic qualifications of the candidate                                |
| Required documents                     | required-docs                        | Documents required for application                                                        |
| Additional info                        | additional-info                      | Additional info regarding the item                                                        |
| Distributor details                    | distributor-details                  | Details of the distributor from the seeker end through which the transaction is happening |

The tags under each tag group are described below

### Tag Groups <a href="#tag-groups" id="tag-groups"></a>

#### Background eligibility <a href="#background-eligibility" id="background-eligibility"></a>

This tag group is available in the `Item` object. This tag group is used to define the background eligibility criteria of a scholarship or grant. The following are the tags that are available under background eligibility:

| Tag code (groups/\[index]/list\[index].descriptor.code | Tag name (groups/\[index]/list\[index]descriptor.name | Tag value (groups/\[index]/list\[index].value                                                                                            | Description                                              |
| ------------------------------------------------------ | ----------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| social-eligibility                                     | Social eligibility                                    | Text. Eg: "OC", "BC", "SC", "ST", "Denotified Nomadic", "Semi Nomadic Tribes", "Landless Agricultural Labourers", "Traditional Artisans" | Social eligibility criteria for the candidate            |
| gender-eligibility                                     | Gender eligibility                                    | Values supported by `Person.gender` to be used here. Eg: "Male", "Female", "Transgender", "Others"                                       | Gender identified by the candidate                       |
| ann-hh-inc                                             | Annual household income                               | Integer. Eg: "200000"                                                                                                                    | Maximum annual household income                          |
| additional-eligibility-criteria                        | Additional eligibility criteria                       | Text                                                                                                                                     | Additional eligibility criteria to be added as free text |

It can be used in search intent to define the various criteria on the expected catalog of results to provide better and relevant results to the user.

**Example 1 : Search for scholarships and grants for a user from the SC or ST community**

```
{
    "message": {
        "intent": {
            "item": {
                "tags": [
                    {
                        "descriptor": {
                            "code": "background-eligibility"
                        },
                        "list": [
                            {
                                "descriptor": {
                                    "code": "social-eligibility"
                                },
                                "value": "SC"
                            },
                            {
                                "descriptor": {
                                    "code": "social-eligibility"
                                },
                                "value": "ST"
                            }
                        ]
                    }
                ]
            }
        }
    }
}
```

It can be used in on\_search response to describe the eligibility criteria of a scholarship or a grant returned in a catalog.

**Example 2 BPP sends an item in the catalog which is only eligible for a female candidate from the SC/ST community with a maximum family income of 500000 per annum**

```
{
    "message": {
        "catalog": {
            "providers": [
                {
                    ...
                    "items": [
                        {
                            ...
                            "tags": [
                                {
                                    "display": true,
                                    "descriptor": {
                                        "code": "background-eligibility",
                                        "name": "Background eligibility"
                                    },
                                    "list": [
                                        {
                                            "descriptor": {
                                                "code": "social-eligibility",
                                                "name": "Social eligibility",
                                                "short_desc": "Social eligibility of the candidate to be eligible"
                                            },
                                            "value": "SC",
                                            "display": true
                                        },
                                        {
                                            "descriptor": {
                                                "code": "social-eligibility",
                                                "name": "Social eligibility",
                                                "short_desc": "Social eligibility of the candidate to be eligible"
                                            },
                                            "value": "ST",
                                            "display": true
                                        },
                                        {
                                            "descriptor": {
                                                "code": "gender-eligibility",
                                                "name": "Gender eligibility",
                                                "short_desc": "Gender of the candidate to be eligible"
                                            },
                                            "value": "Female",
                                            "display": true
                                        },
                                        {
                                            "descriptor": {
                                                "code": "ann-hh-inc",
                                                "name": "Maximum Annual Household Income",
                                                "short_desc": "Maximum Family income per annum above which will render the applicant ineligible"
                                            },
                                            "value": "500000",
                                            "display": true
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    }
}
```

#### Academic eligibility <a href="#academic-eligibility" id="academic-eligibility"></a>

This tag group is available in the `Item` object. This tag group is used to define the academic eligibility criteria of a scholarship or grant. The following are the tags that are available under academic eligibility:

| Tag code (groups/\[index]/list\[index].descriptor.code | Tag name (groups/\[index]/list\[index]descriptor.name | Tag value (groups/\[index]/list\[index].value                     | Description                                                                                                                                                                                                                                    |
| ------------------------------------------------------ | ----------------------------------------------------- | ----------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| course-name                                            | Course name                                           | Text Eg: "Class-X", "Class-XII" etc                               | Name of the course on which academic eligibility is based on                                                                                                                                                                                   |
| course-specialisation                                  | Course specialisation                                 | Text Eg: "Computer Science", "History", "Agriculture Science"     | Specialisation of the course on which academic eligibility is based on                                                                                                                                                                         |
| course-level                                           | Course level                                          | Eg: "Graduate", "Under Graduate"                                  | Level of the course on which academic eligibility is based on                                                                                                                                                                                  |
| course-status                                          | Course status                                         | Enums: "Registered", "In-Progress", "Completed", "Dropped"        | Current status of the course                                                                                                                                                                                                                   |
| issued-by                                              | Issued by                                             | Text. Eg: "Kerala University", "Delhi University", "CBSE", "ICSE" | Name of the organisation issuing the course                                                                                                                                                                                                    |
| min-marks                                              | Minimum marks                                         | Integer. Eg: "400"                                                | Minimum marks required for the course                                                                                                                                                                                                          |
| min-grade                                              | Minimum grade                                         | Text. Eg: "A", "A+", "B", "B+"                                    | Minimum grade required for the course                                                                                                                                                                                                          |
| min-gpa                                                | Minimum GPA                                           | Float. Eg: "6.2", "3.2"                                           | Minimum gpa required for the course                                                                                                                                                                                                            |
| min-percentage                                         | Minimum percentage                                    | Integer. Eg: "80", "90" (No decimal places or percentage symbol)  | Minimum percentage required for the course                                                                                                                                                                                                     |
| mandatory-eligibility                                  | Mandatory eligibility                                 | Boolean. Eg: "true", "false"                                      | Whether the described academic qualification criteria that is mandatory for a job applying or a preference which will increase the chances of the candidate in the selection process. If this tag is not specified it is mandatory by default. |
| additional-eligibility-criteria                        | Additional eligibility criteria                       | Free text                                                         | Additional eligibility criteria                                                                                                                                                                                                                |

It can be used in search intent to define the various criteria on the expected catalog of results to provide better and relevant results to the user.

**Example 1 : Search for scholarships and grants for a user who has passed 10th standard**

```
{
    "message": {
        "intent": {
            "item": {
                "tags": [
                    {
                        "descriptor": {
                            "code": "academic-eligibility"
                        },
                        "list": [
                            {
                                "descriptor": {
                                    "code": "course-name"
                                },
                                "value": "Class-X"
                            }
                        ]
                    }
                ]
            }
        }
    }
}
```

It can be used in on\_search response to describe the eligibility criteria of a scholarship or a grant returned in a catalog.

**Example 2 BPP sends an item in the catalog which is only eligible for a candidate with the following academic qualifications**

* 60% in Class-X
* 60% in Class-XII
* Course Level : Under Graduate
* Current student of Bachelor of Dental Surgery (BDS)

```
{
    "message": {
        "catalog": {
            "providers": [
                {
                    ...
                    "items": [
                        {
                            ...
                            "tags": [
                                {
                                    "display": true,
                                    "descriptor": {
                                        "code": "academic-eligibility",
                                        "name": "Academic Eligibility"
                                    },
                                    "list": [
                                        {
                                            "descriptor": {
                                                "code": "course-name",
                                                "name": "Name of the course"
                                            },
                                            "value": "Class-X",
                                            "display": true
                                        },
                                        {
                                            "descriptor": {
                                                "code": "min-percentage",
                                                "name": "Minimum percentage of marks to be obtained in the course for eligibility"
                                            },
                                            "value": "60",
                                            "display": true
                                        }
                                    ]
                                },
                                {
                                    "display": true,
                                    "descriptor": {
                                        "code": "academic-eligibility",
                                        "name": "Academic Eligibility"
                                    },
                                    "list": [
                                        {
                                            "descriptor": {
                                                "code": "course-name",
                                                "name": "Name of the course"
                                            },
                                            "value": "Class-XII",
                                            "display": true
                                        },
                                        {
                                            "descriptor": {
                                                "code": "min-percentage",
                                                "name": "Minimum percentage of marks to be obtained in the course for eligibility"
                                            },
                                            "value": "60",
                                            "display": true
                                        }
                                    ]
                                },
                                {
                                    "display": true,
                                    "descriptor": {
                                        "code": "academic-eligibility",
                                        "name": "Academic Eligibility"
                                    },
                                    "list": [
                                        {
                                            "descriptor": {
                                                "code": "course-name",
                                                "name": "Name of the course"
                                            },
                                            "value": "Bachelor of Dental Surgery (BDS)",
                                            "display": true
                                        },
                                        {
                                            "descriptor": {
                                                "code": "course-level",
                                                "name": "Level of the course"
                                            },
                                            "value": "Under Graduate",
                                            "display": true
                                        },
                                        {
                                            "descriptor": {
                                                "code": "course-status",
                                                "name": "Status of the course"
                                            },
                                            "value": "In Progress",
                                            "display": true
                                        },
                                        {
                                            "descriptor": {
                                                "code": "min-percentage",
                                                "name": "Minimum percentage of marks to be obtained in the course for eligibility"
                                            },
                                            "value": "60",
                                            "display": true
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    }
}
```

#### Documents required <a href="#documents-required" id="documents-required"></a>

This tag group is available in the `Item` object. This tag group is used to define the documents required for the application of a scholarship or grant. The following are the tags that are available under documents required tag group:

| Tag code (groups/\[index]/list\[index].descriptor.code | Tag name (groups/\[index]/list\[index]descriptor.name | Tag value (groups/\[index]/list\[index].value | Description                                   |
| ------------------------------------------------------ | ----------------------------------------------------- | --------------------------------------------- | --------------------------------------------- |
| mandatory-doc                                          | Mandatory document                                    | Text. Please see examples in JSON below       | Document that should be mandatorily submitted |
| optional-doc                                           | Optional document                                     | Text. Please see examples in JSON below       | Document that is optional                     |

**Example 1 BPP sends an item in the catalog where the application for the same would require the following documents:**

* Applicant Photo
* Proof of Identity
* Proof of Address
* Proof of Income
* Student Bank passbook/Kiosk
* 10th & 12th Marksheet
* Current year fees receipts/fees structure
* Admission Letter / Bonafide certificate from institute
* Latest College Marksheets (Except first year students)

**Optional document**

* PAN No/Domicile certificate

```
{
    "message": {
        "catalog": {
            "providers": [
                {
                    ...
                    "items": [
                        {
                            ...
                            "tags": [
                                {
                                    "display": true,
                                    "descriptor": {
                                        "code": "required-docs",
                                        "name": "Required documents"
                                    },
                                    "list": [
                                        {
                                            "descriptor": {
                                                "code": "mandatory-doc",
                                                "name": "Mandatory document"
                                            },
                                            "value": "Applicant Photo",
                                            "display": true
                                        },
                                        {
                                            "descriptor": {
                                                "code": "mandatory-doc",
                                                "name": "Mandatory document"
                                            },
                                            "value": "Proof of Identity",
                                            "display": true
                                        },
                                        {
                                            "descriptor": {
                                                "code": "mandatory-doc",
                                                "name": "Mandatory document"
                                            },
                                            "value": "Proof of Address",
                                            "display": true
                                        },
                                        {
                                            "descriptor": {
                                                "code": "mandatory-doc",
                                                "name": "Mandatory document"
                                            },
                                            "value": "Proof of Income",
                                            "display": true
                                        },
                                        {
                                            "descriptor": {
                                                "code": "mandatory-doc",
                                                "name": "Mandatory document"
                                            },
                                            "value": "Student Bank passbook/Kiosk",
                                            "display": true
                                        },
                                        {
                                            "descriptor": {
                                                "code": "mandatory-doc",
                                                "name": "Mandatory document"
                                            },
                                            "value": "10th & 12th Marksheet",
                                            "display": true
                                        },
                                        {
                                            "descriptor": {
                                                "code": "mandatory-doc",
                                                "name": "Mandatory document"
                                            },
                                            "value": "Current year fees receipts/fees structure",
                                            "display": true
                                        },
                                        {
                                            "descriptor": {
                                                "code": "mandatory-doc",
                                                "name": "Mandatory document"
                                            },
                                            "value": "Admission Letter / Bonafide certificate from institute",
                                            "display": true
                                        },
                                        {
                                            "descriptor": {
                                                "code": "mandatory-doc",
                                                "name": "Mandatory document"
                                            },
                                            "value": "Latest College Marksheets (Except first year students)",
                                            "display": true
                                        },
                                        {
                                            "descriptor": {
                                                "code": "optional-doc",
                                                "name": "Optional document"
                                            },
                                            "value": "PAN No/Domicile certificate",
                                            "display": true
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    }
}
```

#### Additional info <a href="#additional-info" id="additional-info"></a>

This tag group is available in the `Item` object. This tag group is used to provide additional details of a scholarship or grant. The following are the tags that are available under additional info tag group:

| Tag code (groups/\[index]/list\[index].descriptor.code | Tag name (groups/\[index]/list\[index]descriptor.name | Tag value (groups/\[index]/list\[index].value | Description                                         |
| ------------------------------------------------------ | ----------------------------------------------------- | --------------------------------------------- | --------------------------------------------------- |
| faq-url                                                | FAQ URL                                               | URL                                           | Link to frequently asked questions                  |
| tnc-url                                                | T\&C URL                                              | URL                                           | Link to terms and conditions                        |
| additional-info                                        | Additional info                                       | Text                                          | Any additional info related to scholarship or grant |

**Example 1 An item in the catalog with links its terms and conditions and frequently asked questions:**

```
{
    "message": {
        "catalog": {
            "providers": [
                {
                    ...
                    "items": [
                        {
                            ...
                            "tags": [
                                {
                                    "display": true,
                                    "descriptor": {
                                        "code": "additional-info",
                                        "name": "Additional info"
                                    },
                                    "list": [
                                        {
                                            "descriptor": {
                                                "code": "faq-url",
                                                "name": "FAQ URL",
                                                "short_desc": "Link to FAQ",

                                            },
                                            "value": "https://www.vs.co.in/vs/resources/68/faq/1015_27.html",
                                            "display": true
                                        },
                                        {
                                            "descriptor": {
                                                "code": "tnc-url",
                                                "name": "T&C URL",
                                                "short_desc": "Link to terms & conditions"
                                            },
                                            "value": "https://www.vs.co.in/vs/resources/68/tnc/1015_27.html",
                                            "display": true
                                        }
                                    ]
                                }  
                            ]
                        }
                    ]
                }
            ]
        }
    }
}
```

#### Distributor details <a href="#documents-required" id="documents-required"></a>

This tag group is available in the `Fulfillment` object. This tag group is used to define the details of the distributor from the seeker end through which the transaction is happening. The following are the tags that are available under documents required tag group:

<table><thead><tr><th width="236">Tag code (groups/[index]/list[index].descriptor.code</th><th>Tag name (groups/[index]/list[index]descriptor.name</th><th>Tag value (groups/[index]/list[index].value</th><th>Description</th></tr></thead><tbody><tr><td>distributor-id</td><td>Distributor ID</td><td>Text.</td><td>ID of the distributor</td></tr><tr><td>distributor-name</td><td>Distributor name</td><td>Text.</td><td>Name of the distributor</td></tr><tr><td>distributor-phone</td><td>Distributor phone</td><td>Text.</td><td>Phone number of the distributor</td></tr><tr><td>distributor-email</td><td>Distributor Email</td><td>Text.</td><td>Email of the distributor</td></tr><tr><td>agent-id</td><td>Agent ID</td><td>Text.</td><td>ID of the agent of the distributor</td></tr><tr><td>agent-name</td><td>Agent Name</td><td>Text.</td><td>Name of the agent of the distributor</td></tr><tr><td>agent-phone</td><td>Agent Phone Number</td><td>Text.</td><td>Phone number of the agent of the distributor</td></tr><tr><td>agent-email</td><td>Agent email ID</td><td>Text.</td><td>Email ID of the agent of the distributor</td></tr><tr><td>agent-verified</td><td>Agent Verified</td><td>Boolean. Eg: "true", "false"</td><td>Whether the documents have been verified by the agent</td></tr></tbody></table>


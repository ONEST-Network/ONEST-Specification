# Tags

The TagGroup schema in beckn defines a key-value set that can be listed under a common heading. The schema of the same is shown below:

```yaml
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

They are used to transmit additional information that is not supported in the underlying schema. In work opportunities domain various additional details about a job listing and the candidate applying can be represented using tag groups.

<table><thead><tr><th>Name (groups/[index]/descriptor.name)</th><th width="310.66666666666663">Code groups/[index]/descriptor.code</th><th>Description</th></tr></thead><tbody><tr><td>Academic eligibility</td><td>academic-eligibility</td><td>Academic eligibility required/preferred by the employer</td></tr><tr><td>Job requirements</td><td>job-requirements</td><td>Job description outlined by an employer</td></tr><tr><td>Job responsibilities</td><td>job-responsibilities</td><td>Job responsibilities are the duties and tasks that an employee is expected to perform</td></tr><tr><td>Listing details</td><td>listing-details</td><td>Details regarding the job listing</td></tr><tr><td>Salary information</td><td>salary-info</td><td>Information regarding salary or payment for the job listing</td></tr><tr><td>Employment details</td><td>emp-details</td><td>Current and past employment details of the candidate</td></tr><tr><td>Document</td><td>document</td><td>Documents passed between seeker and provider</td></tr><tr><td>Required documents</td><td>required-docs</td><td>Documents required for application</td></tr></tbody></table>

The tags under each tag group are described below

### Tag Groups <a href="#tag-groups" id="tag-groups"></a>

#### Academic eligibility <a href="#academic-eligibility" id="academic-eligibility"></a>

This tag group is available in the `Item` object. This tag group is used to define the academic eligibility required/preferred for applying to the job listing. The following are the tags that are available under this:

| Tag code (groups/\[index]/list\[index].descriptor.code | Tag name (groups/\[index]/list\[index]descriptor.name | Tag value (groups/\[index]/list\[index].value               | Description                                                                                                                                                                                                                                   |
| ------------------------------------------------------ | ----------------------------------------------------- | ----------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| course-name                                            | Course name                                           | Text Eg: Class-X, Class-XII etc                             | Name of the course on which academic eligibility is based on                                                                                                                                                                                  |
| course-specialisation                                  | Course specialisation                                 | Text Eg: Computer Science, History, Agriculture Science     | Specialisation of the course on which academic eligibility is based on                                                                                                                                                                        |
| course-level                                           | Course level                                          | Eg: Graduate, Under Graduate                                | Level of the course on which academic eligibility is based on                                                                                                                                                                                 |
| course-status                                          | Course status                                         | Registered, In-Progress, Completed, Dropped                 | Current status of the course                                                                                                                                                                                                                  |
| issued-by                                              | Issued by                                             | Text. Eg: Kerala University, Delhi University, CBSE, ICSE   | Name of the organisation issuing the course                                                                                                                                                                                                   |
| min-marks                                              | Minimum marks                                         | Integer. 400                                                | Minimum marks required for the course                                                                                                                                                                                                         |
| min-grade                                              | Minimum grade                                         | Text Eg: A, A+, B, B+                                       | Minimum grade required for the course                                                                                                                                                                                                         |
| min-gpa                                                | Minimum GPA                                           | Float Eg: 6.2, 3,2                                          | Minimum gpa required for the course                                                                                                                                                                                                           |
| min-percentage                                         | Minimum percentage                                    | Integer Eg: 80, 90 (No decimal places or percentage symbol) | Minimum percentage required for the course                                                                                                                                                                                                    |
| mandatory-eligibility                                  | Mandatory eligibility                                 | true/false                                                  | Whether the described academic qualification criteria that is mandatory for a job applying or a preference which will increase the chances of the candidate in the selection process.If this tag is not specified it is mandatory by default. |
| additional-eligibility-criteria                        | Additional eligibility criteria                       | Free text                                                   | Additional eligibility criteria                                                                                                                                                                                                               |

It can be used in on\_select and subsequent responses to describe the required academic eligibility criteria of job listings returned in a catalog.

**Example 1 BPP sends a job listing which is only eligible for a candidate who is has under graduate level education with 60% marks and minimum 60% in class X and class XII and gives preference if candidate has graduate level education**

```json
{
    "message": {
        "order": {
            "provider": {
                    ...
                    "items": [
                    {
                            ...
                            "tags": [
                            {
                                "display": true,
                                "descriptor": {
                                    "code": "academic-eligibility",
                                    "name": "Academic eligibility"
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
                                    },
                                    {
                                        "descriptor": {
                                            "code": "mandatory-eligibility",
                                            "name": "Mandatory Eligibility"
                                        },
                                        "value": "true",
                                        "display": true
                                    }
                                ]
                            },
                            {
                                "display": true,
                                "descriptor": {
                                    "code": "academic-eligibility",
                                    "name": "Academic eligibility"
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
                                    },
                                    {
                                        "descriptor": {
                                            "code": "mandatory-eligibility",
                                            "name": "Mandatory Eligibility"
                                        },
                                        "value": "true",
                                        "display": true
                                    }
                                ]
                            },
                            {
                                "display": true,
                                "descriptor": {
                                    "code": "academic-eligibility",
                                    "name": "Academic eligibility"
                                },
                                "list": [
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
                                            "code": "min-percentage",
                                            "name": "Minimum percentage of marks to be obtained in the course for eligibility"
                                        },
                                        "value": "60",
                                        "display": true
                                    },
                                    {
                                        "descriptor": {
                                            "code": "mandatory-eligibility",
                                            "name": "Mandatory Eligibility"
                                        },
                                        "value": "true",
                                        "display": true
                                    }
                                ]
                            },
                            {
                                "display": true,
                                "descriptor": {
                                    "code": "academic-eligibility",
                                    "name": "Academic eligibility"
                                },
                                "list": [
                                    {
                                        "descriptor": {
                                            "code": "course-level",
                                            "name": "Level of the course"
                                        },
                                        "value": "Graduate",
                                        "display": true
                                    },
                                    {
                                        "descriptor": {
                                            "code": "mandatory-eligibility",
                                            "name": "Mandatory Eligibility"
                                        },
                                        "value": "false",
                                        "display": true
                                    }
                                ]
                            }
                        ]
                    }
                ]
            }
        }
    }
}
```

#### Job requirements <a href="#job-requirements" id="job-requirements"></a>

This tag group is available in the `Item` object. This tag group is used to define the Job requirements outlined by an employer as essential for candidates applying. The following are the tags that are available under this:

| Tag code (groups/\[index]/list\[index].descriptor.code | Tag name (groups/\[index]/list\[index]descriptor.name | Tag value (groups/\[index]/list\[index].value | Description                       |
| ------------------------------------------------------ | ----------------------------------------------------- | --------------------------------------------- | --------------------------------- |
| req-experience                                         | Required experience                                   | Float 3.5,4                                   | Required work experience in years |
| req-prof-skill                                         | Required professional skill                           | Free text                                     | Skills required for the role      |

It can be used in on\_select and subsequent responses to describe the requirements of the job listing returned.

**Example 1 BPP sends a job listing which is will give preference if candidate has graduate level education**

```json
{
    "message": {
        "order": {
            "provider": {
                    ...
                    "items": [
                    {
                            ...
                            "tags": [
                            {
                                "display": true,
                                "descriptor": {
                                    "code": "job-requirements",
                                    "name": "Job requirements"
                                },
                                "list": [
                                    {
                                        "descriptor": {
                                            "code": "req-experience",
                                            "name": "Required work experience in years"
                                        },
                                        "value": "2.5",
                                        "display": true
                                    },
                                    {
                                        "descriptor": {
                                            "code": "req-prof-skill",
                                            "name": "Skills required for the role"
                                        },
                                        "value": "android-development",
                                        "display": true
                                    },
                                    {
                                        "descriptor": {
                                            "code": "req-prof-skill",
                                            "name": "Skills required for the role"
                                        },
                                        "value": "dev-ops",
                                        "display": true
                                    },
                                    {
                                        "descriptor": {
                                            "code": "req-prof-skill",
                                            "name": "Additional skills required for the job"
                                        },
                                        "value": "You have 8+ years of engineering experience, predominantly in shipping user-facing production features",
                                        "display": true
                                    }
                                ]
                            }
                        ]
                    }
                ]
            }
        }
    }
}
```

#### Job responsibilities <a href="#job-responsibilities" id="job-responsibilities"></a>

This tag group is available in the `Item` object. This tag group is used to define the job responsibilities that an employee is expected to perform as part of their role within an organization. The following are the tags that are available under this:

| Tag code (groups/\[index]/list\[index].descriptor.code | Tag name (groups/\[index]/list\[index]descriptor.name | Tag value (groups/\[index]/list\[index].value | Description                           |
| ------------------------------------------------------ | ----------------------------------------------------- | --------------------------------------------- | ------------------------------------- |
| responsibility                                         | Responsibility                                        | Free text                                     | Description of responsibility as text |

It can be used in on\_select and subsequent responses to describe the responsibilities of the job listing returned.

**Example 1 BPP sends a job listing with the responsibilities associated with the role**

```json
{
    "message": {
        "order": {
            "provider": {
                    ...
                    "items": [
                    {
                            ...
                            "tags": [
                            {
                                "display": true,
                                "descriptor": {
                                    "code": "job-responsibilities",
                                    "name": "Job responsibilities"
                                },
                                "list": [
                                    {
                                        "descriptor": {
                                            "code": "responsibility",
                                            "name": "Responsibility"
                                        },
                                        "value": "Build frontend experiences for our tools (Web, PWA and React Native)",
                                        "display": true
                                    },
                                    {
                                        "descriptor": {
                                            "code": "responsibility",
                                            "name": "Responsibility"
                                        },
                                        "value": "Articulate a long term technical direction and vision for building, maintaining, and scaling our web and mobile platforms",
                                        "display": true
                                    },
                                    {
                                        "descriptor": {
                                            "code": "responsibility",
                                            "name": "Responsibility"
                                        },
                                        "value": "Create trustworthy user experiences by building interfaces that are simple, easy to comprehend, performant and reliable using modern tools like React, React Native, Typescript, Node.js, Jest and Webpack.",
                                        "display": true
                                    },
                                    {
                                        "descriptor": {
                                            "code": "responsibility",
                                            "name": "Responsibility"
                                        },
                                        "value": "Mentor and train other team members on design techniques and coding standards.",
                                        "display": true
                                    }
                                ]
                            }
                        ]
                    }
                ]
            }
        }
    }
}
```

#### Listing details <a href="#listing-details" id="listing-details"></a>

This tag group is available in the `Item` object. This tag group is used to define additional details regarding the job listing. The following are the tags that are available under this:

| Tag code (groups/\[index]/list\[index].descriptor.code | Tag name (groups/\[index]/list\[index]descriptor.name | Tag value (groups/\[index]/list\[index].value                        | Description                                                                            |
| ------------------------------------------------------ | ----------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| industry-type                                          | Industry type                                         | Text. Eg: Electric Vehicles, IT Services & Consulting, Manufacturing | Sector and domain to which the job listing belongs to                                  |
| department                                             | Department                                            | Text. Eg: Marketing, Assembly, QA                                    | A department or unit within a company                                                  |
| employment-type                                        | Employment type                                       | Enums: full-time, part-time, temporary, contract, consultant         | Nature of employment contract                                                          |
| job-role                                               | Job role                                              | Text. Eg: Developer, Assembly Line Operator, Technician etc          | A job role or title that would be assigned to the person employed against this listing |

It can be used in on\_select and subsequent responses to describe the details of the job listing returned.

**Example 1 BPP sends a job listing with the details of the same**

```json
{
    "message": {
        "order": {
            "provider": {
                    ...
                    "items": [
                    {
                            ...
                            "tags": [
                            {
                                "display": true,
                                "descriptor": {
                                    "code": "listing-details",
                                    "name": "Listing details"
                                },
                                "list": [
                                    {
                                        "descriptor": {
                                            "code": "industry-type",
                                            "name": "Industry type"
                                        },
                                        "value": "IT Services & Consulting",
                                        "display": true
                                    },
                                    {
                                        "descriptor": {
                                            "code": "department",
                                            "name": "Department"
                                        },
                                        "value": "Engineering - Software & QA",
                                        "display": true
                                    },
                                    {
                                        "descriptor": {
                                            "code": "employment-type",
                                            "name": "Employment type"
                                        },
                                        "value": "full-time",
                                        "display": true
                                    },
                                    {
                                        "descriptor": {
                                            "code": "job-role",
                                            "name": "Job role"
                                        },
                                        "value": "DevOps Engineer",
                                        "display": true
                                    }
                                ]
                            }
                        ]
                    }
                ]
            }
        }
    }
}
```

#### Salary information <a href="#salary-information" id="salary-information"></a>

This tag group is available in the `Item` object. This tag group is used to define salary or pay information regarding the job listing. The following are the tags that are available under this:

| Tag code (groups/\[index]/list\[index].descriptor.code | Tag name (groups/\[index]/list\[index]descriptor.name | Tag value (groups/\[index]/list\[index].value                                      | Description                                   |
| ------------------------------------------------------ | ----------------------------------------------------- | ---------------------------------------------------------------------------------- | --------------------------------------------- |
| gross-min                                              | Minimum gross pay                                     | Integer. Eg: 100000                                                                | Minimum gross pay offered for the job listing |
| gross-max                                              | Maximum gross pay                                     | Integer Eg: 700000                                                                 | Maximum gross pay offered for the job listing |
| allowance                                              | Allowance                                             | Text. Eg: "Food allowance of Rs.200 per day", "Travel allowance of Rs.500 per day" | Allowance related info for the job listing    |
| additional-info                                        | Additional info                                       | Text                                                                               | Any additional info related to salary         |

It can be used in on\_select and subsequent responses to describe the salary or pay information of the job listing returned.

**Example 1 BPP sends a job listing with the salary range**

```json
{
    "message": {
        "order": {
            "provider": {
                    ...
                    "items": [
                    {
                            ...
                            "tags": [
                            {
                                "display": true,
                                "descriptor": {
                                    "code": "salary-info",
                                    "name": "Salary information"
                                },
                                "list": [
                                    {
                                        "descriptor": {
                                            "code": "gross-min",
                                            "name": "Minimum gross pay"
                                        },
                                        "value": "900000",
                                        "display": true
                                    },
                                    {
                                        "descriptor": {
                                            "code": "gross-max",
                                            "name": "Maximum gross pay"
                                        },
                                        "value": "1200000",
                                        "display": true
                                    }
                                ]
                            }
                        ]
                    }
                ]
            }
        }
    }
}
```

#### Employment details <a href="#employment-details" id="employment-details"></a>

This tag group is available in the `Person` object. This tag group is used to define the current employment details of the candidate. The following are the tags that are available under this:

| Tag code (groups/\[index]/list\[index].descriptor.code | Tag name (groups/\[index]/list\[index]descriptor.name | Tag value (groups/\[index]/list\[index].value | Description                                   |
| ------------------------------------------------------ | ----------------------------------------------------- | --------------------------------------------- | --------------------------------------------- |
| current-salary                                         | Current salary                                        | Integer. Eg: 300000                           | Current salary of the candidate               |
| expected-salary                                        | Expected salary                                       | Integer. Eg: 5000000                          | Expected salary                               |
| current-employer                                       | Current employer                                      | Text. Eg: "ABC Tech"                          | Name of the current employer of the candidate |
| total-experience                                       | Total experience                                      | Float. Eg: 4.5, 5                             | Work experience of the candidate in years     |

It can be used in init and subsequent calls by the BAP to send details regarding the candidates current employment to the BPP.

**Example 1 : Initialize a job application by sending the candidates current employment information**

```json
{
    "message": {
        "order": {
            "provider": {
                    ...
                    "fulfillments": [
                    {
                        ...
                        "customer": {
                            "person": {
                                ...
                                "tags": [
                                    {
                                        "descriptor": {
                                            "code": "emp-details",
                                            "name": "Current employment details"
                                        },
                                        "list": [
                                            {
                                                "descriptor": {
                                                    "code": "current-salary"
                                                },
                                                "value": "900000"
                                            },
                                            {
                                                "descriptor": {
                                                    "code": "expected-salary"
                                                },
                                                "value": "1200000"
                                            },
                                            {
                                                "descriptor": {
                                                    "code": "current-employer"
                                                },
                                                "value": "ABC Tech"
                                            },
                                            {
                                                "descriptor": {
                                                    "code": "total-experience"
                                                },
                                                "value": "4"
                                            }
                                        ]
                                    }
                                ]
                            }
                        }
                    }
                ]
            }
        }
    }
}
```

It can be used in search intent to define the details/expectations of the candidate to provide better and relevant job listings to the user.

**Example 2 : Search for job listings for a candidate with 4 years of experience and a salary expectation of 1000000**

```json
{
    "message": {
        "intent": {
            "fulfillment": {
                "customer":{
                    "person":{
                        "tags": [
                            {
                                "descriptor": {
                                    "code": "emp-details"
                                },
                                "list": [
                                    {
                                        "descriptor": {
                                            "code": "expected-salary"
                                        },
                                        "value": "1000000"
                                    },
                                    {
                                        "descriptor": {
                                            "code": "total-experience"
                                        },
                                        "value": "4"
                                    }
                                ]
                            }
                        ]
                    }
                }
            }
        }
    }
}
```

#### Documents <a href="#documents" id="documents"></a>

This tag group is available in the `Person` and `Fulfillment` object. This tag group is used to define the documents sent by the candidate to the provider when used in the `Person` object and by the provider to send documents to the user in `Fulfillment` object. The following are the tags that are available under this:

| Tag code (groups/\[index]/list\[index].descriptor.code | Tag name (groups/\[index]/list\[index]descriptor.name | Tag value (groups/\[index]/list\[index].value                               | Description                           |
| ------------------------------------------------------ | ----------------------------------------------------- | --------------------------------------------------------------------------- | ------------------------------------- |
| doc-type                                               | Document type                                         | Text. Eg: "resume", "provisional-offer-letter"                              | What type of document is being shared |
| link                                                   | Link                                                  | URL. Eg: "[https://example.com/resume.pdf](https://example.com/resume.pdf)" | Link to the document                  |
| file-format                                            | File format                                           | Text. Eg: "pdf"                                                             | Format of the document being shared   |

**Example 1 : Initialize a job application by sending the resume of the candidate**

```json
{
    "message": {
        "order": {
            "provider": {
                    ...
                    "fulfillments": [
                    {
                        ...
                        "customer": {
                            "person": {
                                ...
                                "tags": [
                                    {
                                        "descriptor": {
                                            "code": "documents",
                                            "name": "Documents"
                                        },
                                        "list": [
                                            {
                                                "descriptor": {
                                                    "code": "doc-type"
                                                },
                                                "value": "resume"
                                            },
                                            {
                                                "descriptor": {
                                                    "code": "link"
                                                },
                                                "value": "https://example.com/resume.pdf"
                                            },
                                            {
                                                "descriptor": {
                                                    "code": "file-format"
                                                },
                                                "value": "pdf"
                                            }
                                        ]
                                    }
                                ]
                            }
                        }
                    }
                ]
            }
        }
    }
}
```

**Example 2 : Provider sends the provisional offer letter to the candidate.**

```json
{
    "message": {
        "order": {
            "provider": {
                "fulfillments": [
                    {
                        "tags": [
                            {
                                "descriptor": {
                                    "code": "documents",
                                    "name": "Documents"
                                },
                                "list": [
                                    {
                                        "descriptor": {
                                            "code": "doc-type"
                                        },
                                        "value": "provisional-offer-letter"
                                    },
                                    {
                                        "descriptor": {
                                            "code": "link"
                                        },
                                        "value": "https://example.com/offer.pdf"
                                    },
                                    {
                                        "descriptor": {
                                            "code": "file-format"
                                        },
                                        "value": "pdf"
                                    }
                                ]
                            }
                        ]
                    }
                ]
            }
        }
    }
}
```

#### Documents required <a href="#documents-required" id="documents-required"></a>

This tag group is available in the `Item` object. This tag group is used to define the documents required for the job application. The following are the tags that are available under documents required tag group:

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

```json
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




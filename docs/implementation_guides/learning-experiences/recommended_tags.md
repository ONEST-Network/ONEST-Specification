# Tag Groups for Learning Experiences domain in ONEST

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


They are used to transmit additional information that is not supported in the underlying schema. In work opportunities domain various additional details about a job listing and the candidate applying can be represented using tag groups.

| Name `(groups/[index]/descriptor.name)` | Code `groups/[index]/descriptor.code` | Description                                                                                                                        |
| ----------------------------------------- | --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Content metadata | content-metadata | Metadata about the content |
| Course Completion Details | course-completion-details | Details shared to the user on course completion |

The tags under each tag group are described below

## Tag Groups

### Content metadata

This tag group is available in the `Item` object. This tag group is used to define the metadata about the course. The following are the tags that are available under this:
| Tag code `(groups/[index]/list[index].descriptor.code` | Tag name `(groups/[index]/list[index]descriptor.name` | Tag value `(groups/[index]/list[index].value` | Description |
| -------------------------------------------------------- | ------------------------------------------------------- | ----------------------------------------------- | ------------------------------------------------------------- |
| learner-level | Learner level | "Beginner", "Intermediate", "Advanced" | Learner level for the course |
| prerequisite | Prerequisite | Text. |Prerequisite required for the course |
| lang-code | Language code | ISO 639-1:2002 codes. Eg: "en" |Standard language codes for the course as per ISO 639-1:2002|
| course-duration | Course duration | ISO duration format. Eg: "P20H" | Duration of the course in ISO duration format|

It can be used in on_search and subsequent responses to describe the metadata of a course offered by a Provider in their catalog.

#### Example BPP sends a course with associated metadata.

```
{
    "message": {
        "catalog": {
            ...
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
                                        "code": "content-metadata",
                                        "name": "Content Metadata"
                                    },
                                    "list": [
                                        {
                                            "descriptor": {
                                                "code": "learner-level",
                                                "name": "Learner level"
                                            },
                                            "value": "Advanced"
                                        },
                                        {
                                            "descriptor": {
                                                "code": "learning-objective",
                                                "name": "Learning objective"
                                            },
                                            "value": "By the end of the course, learners will confidently navigate everyday conversations, demonstrating improved fluency, cultural awareness, and effective communication skills."
                                        },
                                        {
                                            "descriptor": {
                                                "code": "learning-objective",
                                                "name": "Learning objective"
                                            },
                                            "value": "Know useful phrases and sentences that can be used in everyday life."
                                        },
                                        {
                                            "descriptor": {
                                                "code": "prerequisite",
                                                "name": "Prerequisite"
                                            },
                                            "value": "Access to a computer or internet to access the course online."
                                        },
                                        {
                                            "descriptor": {
                                                "code": "prerequisite",
                                                "name": "Prerequisite"
                                            },
                                            "value": "Should have a basic understanding of English"
                                        },
                                        {
                                            "descriptor": {
                                                "code": "lang-code",
                                                "name": "Language code"
                                            },
                                            "value": "en"
                                        },
                                        {
                                            "descriptor": {
                                                "code": "course-duration",
                                                "name": "Course duration"
                                            },
                                            "value": "P20H"
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

### Course completion details

This tag group is available in the `Item` object. This tag group is used to return certificates or other details on completion of a course. The following are the tags that are available under this:
| Tag code `(groups/[index]/list[index].descriptor.code` | Tag name `(groups/[index]/list[index]descriptor.name` | Tag value `(groups/[index]/list[index].value` | Description |
| -------------------------------------------------------- | ------------------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- |
| course-certificate | Course certificate | URL to the certificate. | Certificate that will be returned to the user on completion |
| course-badge | Course badge | URL to the badge image. | An image badge that can be displayed on the user profile |
| completion-timestamp | Completion timestamp | Timestamp. Eg: "2024-02-09T04:59:29.914Z" | Timestamp of when the course was completed |

It can be used in on_select and subsequent responses to describe the requirements of the job listing returned.

#### Example 1 BPP sends the link to the certificate and badge to the user on successful completion of the course in status API.

```
{
    "message": {
        "order": {
            "provider": {
                    "items": [
                    {
                            "tags": [
                            {
                                "display": true,
                                "descriptor": {
                                    "code": "course-completion-details",
                                    "name": "Course completion details"
                                },
                                "list": [
                                    {
                                        "descriptor": {
                                            "code": "course-certificate",
                                            "name": "Course Certificate"
                                        },
                                        "value": "https://bpp.example.com/user-1231/certificate.pdf",
                                        "display": true
                                    },
                                    {
                                        "descriptor": {
                                            "code": "course-badge",
                                            "name": "Course badge"
                                        },
                                        "value": "https://bpp.example.com/user-1231/badge.png",
                                        "display": true
                                    },
                                    {
                                        "descriptor": {
                                            "code": "completion-timestamp",
                                            "name": "Completion Timestamp"
                                        },
                                        "value": "2024-02-09T04:59:29.914Z",
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



This tag group is available in the `Person` object. This tag group is used to define the current employment details of the candidate. The following are the tags that are available under background eligibility:
| Tag code `(groups/[index]/list[index].descriptor.code` | Tag name `(groups/[index]/list[index]descriptor.name` | Tag value `(groups/[index]/list[index].value` | Description |
| -------------------------------------------------------- | ------------------------------------------------------- | ----------------------------------------------- | --------------------------------------------- |
| current-salary                                           | Current salary                                          | Integer. Eg: 300000                                         | Current salary of the candidate               |
| expected-salary                                          | Expected salary                                         | Integer. Eg: 5000000                                        | Expected salary                               |
| current-employer                                         | Current employer                                        | Text. Eg: "ABC Tech"                                    | Name of the current employer of the candidate |
| total-experience                                               | Total experience                                              | Float. Eg: 4.5, 5                                                 | Work experience of the candidate in years     |

It can be used in init and subsequent calls by the BAP to send details regarding the candidates current employment to the BPP.

#### Example 1 : Initialize a job application by sending the candidates current employment information 

```
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

#### Example 2 : Search for job listings for a candidate with 4 years of experience and a salary expectation of 1000000 

```
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

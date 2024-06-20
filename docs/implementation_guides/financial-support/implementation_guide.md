# Financial Support

### Use-case

A provider platform which acts as BPP provides scholarships and a seeker platform which acts as BAP will help the people to avail scholarships through its platform.

### Flow Diagram

<figure><img src="../../assets/financial-support-flow.jpg" alt=""><figcaption></figcaption></figure>

### API Mapping and Sample JSON's

Please refer to the tags subsection for detailed explanations on the tags used.

<details>

<summary>Search API - Search by gender</summary>

```json
{
    "context": {
        "domain": "onest:financial-support",
        "action": "search",
        "version": "1.1.0",
        "bap_id": "sample.bap.io",
        "bap_uri": "https://sample.bap.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-022723112309",
        "message_id": "a9aaecca-10b7-4d19-b640-b047a7c60009",
        "timestamp": "2023-02-06T09:55:41.161Z",
        "ttl": "PT10M"
    },
    "message": {
        "intent": {
            "fulfillment": {
                "customer": {
                    "person": {
                        "gender": "Female"
                    }
                }
            }
        }
    }
}
```

</details>

<details>

<summary>Search API - Search by scholarship name</summary>

```json
{
    "context": {
        "domain": "onest:financial-support",
        "action": "search",
        "version": "1.1.0",
        "bap_id": "sample.bap.io",
        "bap_uri": "https://sample.bap.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-022723112309",
        "message_id": "a9aaecca-10b7-4d19-b640-b047a7c60009",
        "timestamp": "2023-02-06T09:55:41.161Z",
        "ttl": "PT10M"
    },
   "message": {
      "intent": {
         "item": {
            "descriptor": {
               "name": "scholarship for undergraduate"
            }
         }
      }
   }
}
```

</details>

<details>

<summary>Search API - Search by gender and scholarship name</summary>

```json
{
    "context": {
        "domain": "onest:financial-support",
        "action": "search",
        "version": "1.1.0",
        "bap_id": "sample.bap.io",
        "bap_uri": "https://sample.bap.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-022723112309",
        "message_id": "a9aaecca-10b7-4d19-b640-b047a7c60009",
        "timestamp": "2023-02-06T09:55:41.161Z",
        "ttl": "PT10M"
    },
   "message": {
      "intent": {
         "item": {
            "descriptor": {
               "name": "scholarship for undergraduate"
            }
         },
         "fulfillment": {
            "customer": {
               "person": {
                  "gender": "Female"
               }
            }
         }
      }
   }
}
```

</details>

<details>

<summary>Search API - Search by eligibility criteria</summary>

Here the user is searching for scholarships and grants for a user from the SC or ST community, who has passed 10th standard.

```json
{
    "context": {
        "domain": "onest:financial-support",
        "action": "search",
        "version": "1.1.0",
        "bap_id": "sample.bap.io",
        "bap_uri": "https://sample.bap.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-022723112309",
        "message_id": "a9aaecca-10b7-4d19-b640-b047a7c60009",
        "timestamp": "2023-02-06T09:55:41.161Z",
        "ttl": "PT10M"
    },
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
                    },
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

</details>

<details>

<summary>Search API - Search by location</summary>

```json
{
    "context": {
        "domain": "onest:financial-support",
        "action": "search",
        "version": "1.1.0",
        "bap_id": "sample.bap.io",
        "bap_uri": "https://sample.bap.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-022723112309",
        "message_id": "a9aaecca-10b7-4d19-b640-b047a7c60009",
        "timestamp": "2023-02-06T09:55:41.161Z",
        "ttl": "PT10M"
    },
    "message": {
        "intent": {
            "provider": {
                "locations": [
                    {
                        "city": {
                            "name": "Bangalore",
                            "code": "std:080"
                        },
                        "state": {
                            "name": "Karnataka",
                            "code": "IN-KA"
                        },
                        "country": {
                            "name": "India",
                            "code": "IN"
                        }
                    }
                ]
            }
        }
    }
}
```

The seeker apps can provide geographical locations where it requires scholarships based out of. Here country object is optional as state ISO code already denotes the country code as well. Please note caching by country alone may result in the influx of high number of listings.

</details>

Searches may be used by the seeker apps to cache responses basis the intent as well.&#x20;

2. BPP will create a catalogue of scholarships with matching criteria and sends it in on\_search request.

<details>

<summary>On Search API</summary>

```json
{
    "context": {
        "domain": "onest:financial-support",
        "action": "on_search",
        "timestamp": "2023-08-02T07:21:58.448Z",
        "ttl": "PT10M",
        "version": "1.1.0",
        "bap_id": "sample.bap.io",
        "bap_uri": "https://sample.bap.io",
        "bpp_id": "sample.bpp.io",
        "bpp_uri": "https://sample.bpp.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
        "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
    },
    "message": {
        "catalog": {
            "descriptor": {
                "name": "Protean DSEP Scholarships and Grants BPP Platform"
            },
            "providers": [
                {
                    "id": "BX213573733",
                    "descriptor": {
                        "name": "XYZ Education Foundation",
                        "short_desc": "Short Description about the Foundation",
                        "images": [
                            {
                                "url": "https://xyz.com/logo"
                            }
                        ]
                    },
                    "categories": [
                        {
                            "id": "DSEP_CAT_1",
                            "descriptor": {
                                "code": "ug",
                                "name": "Under Graduate"
                            }
                        }
                    ],
                    "fulfillments": [
                        {
                            "id": "DSEP_FUL_63587501",
                            "tracking": false
                        }
                    ],
                    "locations": [
                        {
                            "id": "L1",
                            "city": {
                                "name": "Pune",
                                "code": "std:020"
                            },
                            "state": {
                                "name": "Maharastra",
                                "code": "MH"
                            }
                        },
                        {
                            "id": "L2",
                            "city": {
                                "name": "Thane",
                                "code": "std:022"
                            },
                            "state": {
                                "name": "Maharastra",
                                "code": "MH"
                            }
                        }
                    ],
                    "items": [
                        {
                            "id": "SCM_63587501",
                            "descriptor": {
                                "name": "XYZ Education Scholarship for Undergraduate Students",
                                "long_desc": "XYZ Education Scholarship for Undergraduate Students"
                            },
                            "price": {
                                "currency": "INR",
                                "value": "1000"
                            },
                            "time": {
                                "range": {
                                    "start": "2023-01-03T13:23:01+00:00",
                                    "end": "2023-02-03T13:23:01+00:00"
                                }
                            },
                            "rateable": false,
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
                                            "value": "In-Progress",
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
                                                "code": "optional-doc",
                                                "name": "Optional document"
                                            },
                                            "value": "PAN No/Domicile certificate",
                                            "display": true
                                        }
                                    ]
                                },
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
                                                "short_desc": "Link to FAQ"
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
                            ],
                            "category_ids": [
                                "DSEP_CAT_1"
                            ],
                            "location_ids": [
                                "L1",
                                "L2"
                            ],
                            "fulfillment_ids": [
                                "DSEP_FUL_63587501"
                            ]
                        }
                    ],
                    "rateable": false
                }
            ]
        }
    }
}
```

</details>

3. BAP will receive the on\_search request and displays the list of scholarships/grants to the user. Once the user chooses one, BAP will make select API with item ID to get the complete details about the item and re-confirm its availability.JSON&#x20;

<details>

<summary>Select API</summary>

```json
{
    "context": {
        "domain": "onest:financial-support",
        "action": "select",
        "timestamp": "2023-08-02T07:21:58.448Z",
        "ttl": "PT10M",
        "version": "1.1.0",
        "bap_id": "sample.bap.io",
        "bap_uri": "https://sample.bap.io",
        "bpp_id": "sample.bpp.io",
        "bpp_uri": "https://sample.bpp.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
        "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
    },
    "message": {
        "order": {
            "items": [
                {
                    "id": "SCM_63587501"
                }
            ],
            "provider": {
                "id": "BX213573733"
            }
        }
    }
}
```

</details>

3. BPP will receive the select request and check if the item is still valid. If the listing is still valid, BPP will send the on\_select call with complete details of the job listing.

<details>

<summary>On Select API</summary>

```json
{
    "context": {
        "domain": "onest:financial-support",
        "action": "on_select",
        "timestamp": "2023-08-02T07:21:58.448Z",
        "ttl": "PT10M",
        "version": "1.1.0",
        "bap_id": "sample.bap.io",
        "bap_uri": "https://sample.bap.io",
        "bpp_id": "sample.bpp.io",
        "bpp_uri": "https://sample.bpp.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
        "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
    },
    "message": {
        "order": {
            "provider": {
                "id": "471",
                "descriptor": {
                    "name": "XYZ Education Foundation",
                    "short_desc": "Short Description about the Foundation",
                    "images": [
                        {
                            "url": "https://xyz.com/logo"
                        }
                    ]
                },
                "locations": [
                    {
                        "id": "L1",
                        "city": {
                            "name": "Pune",
                            "code": "std:020"
                        },
                        "state": {
                            "name": "Maharastra",
                            "code": "MH"
                        }
                    },
                    {
                        "id": "L2",
                        "city": {
                            "name": "Thane",
                            "code": "std:022"
                        },
                        "state": {
                            "name": "Maharastra",
                            "code": "MH"
                        }
                    }
                ],
                "rateable": false
            },
            "items": [
                {
                    "id": "SCM_63587501",
                    "descriptor": {
                        "name": "XYZ Education Scholarship for Undergraduate Students",
                        "long_desc": "XYZ Education Scholarship for Undergraduate Students"
                    },
                    "price": {
                        "currency": "INR",
                        "value": "1000"
                    },
                    "time": {
                        "range": {
                            "start": "2023-01-03T13:23:01+00:00",
                            "end": "2023-02-03T13:23:01+00:00"
                        }
                    },
                    "rateable": false,
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
                                    "value": "In-Progress",
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
                                        "code": "optional-doc",
                                        "name": "Optional document"
                                    },
                                    "value": "PAN No/Domicile certificate",
                                    "display": true
                                }
                            ]
                        },
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
                                        "short_desc": "Link to FAQ"
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
                    ],
                    "location_ids": [
                        "L1",
                        "L2"
                    ],
                    "fulfillment_ids": [
                        "VSP_FUL_1113"
                    ]
                }
            ],
            "fulfillments": [
                {
                    "id": "VSP_FUL_1113",
                    "tracking": false
                }
            ],
            "quote": {
                "price": {
                    "currency": "INR",
                    "value": "250000"
                },
                "breakup": [
                    {
                        "title": "Tution fee",
                        "price": {
                            "currency": "INR",
                            "value": "150000"
                        }
                    },
                    {
                        "title": "Hostel fee",
                        "price": {
                            "currency": "INR",
                            "value": "50000"
                        }
                    },
                    {
                        "title": "Books",
                        "price": {
                            "currency": "INR",
                            "value": "50000"
                        }
                    }
                ]
            }
        }
    }
}
```

</details>

3. BAP will send the init request with basic custom details to initialize the scholarship application process.

<details>

<summary>Init API</summary>

```json
{
   "context": {
      "domain": "onest:financial-support",
      "action": "init",
      "timestamp": "2023-08-02T07:21:58.448Z",
      "ttl": "PT10M",
      "version": "1.1.0",
      "bap_id": "sample.bap.io",
      "bap_uri": "https://sample.bap.io",
      "bpp_id": "sample.bpp.io",
      "bpp_uri": "https://sample.bpp.io",
      "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
      "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
   },
   "message": {
      "order": {
         "items": [
            {
               "id": "SCM_63587501"
            }
         ],
         "provider": {
            "id": "BX213573733"
         },
         "billing": {
            "name": "Manjunath",
            "organization": {
               "descriptor": {
                  "name": "Namma Yatri",
                  "code": "nammayatri.in"
               },
               "contact": {
                  "phone": "+91-8888888888",
                  "email": "scholarships@nammayatri.in"
               }
            },
            "address": "No 27, XYZ Lane, etc",
            "phone": "+91-9999999999"
         },
         "fulfillments": [
            {
               "customer": {
                  "id": "aadhaar:798677675565",
                  "person": {
                     "name": "Jane Doe",
                     "age": "13",
                     "gender": "female"
                  },
                  "contact": {
                     "phone": "+91-9663088848",
                     "email": "jane.doe@example.com"
                  }
               }
            }
         ],
         "payments" : [
            {
               "params" :{
                  "bank_code": "IFSC_Code_Of_the_bank",
                  "bank_account_number" :"121212121212",
                  "bank_account_name" : "Account Holder Name"
               }

            }
         ]

      }
   }
}
```

</details>

4. If BPP wants to collect additional details of the user, it will send an xinput form in the on\_init request.\
   \
   If BPP has multiple forms to collect the data, it will make on\_init request with the form number(current index) and total number of forms(max index). BPP should generate the xinput form with transaction id(request.context.transaction\_id) so that the forms can be tagged with an order lifecycle.\
   \
   BAP should render the xinput form on the UI and collect all the details.\
   \
   If there are no required xinput forms, the BAP can confirm the order via /confirm API.\
   \
   [Example](https://github.com/ONEST-Network/ONEST-Specification/blob/main/docs/ONEST-001-Suggested-xInput-Form-Fields.md#example)

<details>

<summary>On Init API - Step 1</summary>

```json
{
    "context": {
        "domain": "onest:financial-support",
        "action": "on_init",
        "timestamp": "2023-08-02T07:21:58.448Z",
        "ttl": "PT10M",
        "version": "1.1.0",
        "bap_id": "sample.bap.io",
        "bap_uri": "https://sample.bap.io",
        "bpp_id": "sample.bpp.io",
        "bpp_uri": "https://sample.bpp.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
        "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
    },
    "message": {
        "order": {
            "provider": {
                "id": "471",
                "descriptor": {
                    "name": "XYZ Education Foundation",
                    "short_desc": "Short Description about the Foundation",
                    "images": [
                        {
                            "url": "https://xyz.com/logo"
                        }
                    ]
                },
                "locations": [
                    {
                        "id": "L1",
                        "city": {
                            "name": "Pune",
                            "code": "std:020"
                        },
                        "state": {
                            "name": "Maharastra",
                            "code": "MH"
                        }
                    },
                    {
                        "id": "L2",
                        "city": {
                            "name": "Thane",
                            "code": "std:022"
                        },
                        "state": {
                            "name": "Maharastra",
                            "code": "MH"
                        }
                    }
                ],
                "rateable": false
            },
            "items": [
                {
                    "id": "SCM_63587501",
                    "descriptor": {
                        "name": "XYZ Education Scholarship for Undergraduate Students",
                        "long_desc": "XYZ Education Scholarship for Undergraduate Students"
                    },
                    "price": {
                        "currency": "INR",
                        "value": "1000"
                    },
                    "time": {
                        "range": {
                            "start": "2023-01-03T13:23:01+00:00",
                            "end": "2023-02-03T13:23:01+00:00"
                        }
                    },
                    "xinput": {
                        "required": true,
                        "head": {
                            "descriptor": {
                                "name": "Application Form"
                            },
                            "index": {
                                "min": 0,
                                "cur": 0,
                                "max": 3
                            },
                            "headings": [
                                "Personal Details",
                                "Educational Details",
                                "Financial Information",
                                "Review & Submit"
                            ]
                        },
                        "form": {
                            "mime_type": "text/html",
                            "url": "https://6vs8xnx5i7.vidyasaarathi.co.in/loans-kyc/xinput/formid/a23f2fdfbbb8ac402bfd54f",
                            "resubmit": false,
                            "auth": {
                                "descriptor": {
                                    "code": "jwt"
                                },
                                "value": "eyJhbGciOiJIUzI.eyJzdWIiOiIxMjM0NTY3O.SflKxwRJSMeKKF2QT4"
                            }
                        }
                    },
                    "rateable": false,
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
                                    "value": "In-Progress",
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
                                        "code": "optional-doc",
                                        "name": "Optional document"
                                    },
                                    "value": "PAN No/Domicile certificate",
                                    "display": true
                                }
                            ]
                        },
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
                                        "short_desc": "Link to FAQ"
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
                    ],
                    "location_ids": [
                        "L1",
                        "L2"
                    ],
                    "fulfillment_ids": [
                        "VSP_FUL_1113"
                    ]
                }
            ],
            "billing": {
                "name": "Manjunath",
                "organization": {
                    "descriptor": {
                        "name": "Namma Yatri",
                        "code": "nammayatri.in"
                    },
                    "contact": {
                        "phone": "+91-8888888888",
                        "email": "scholarships@nammayatri.in"
                    }
                },
                "address": "No 27, XYZ Lane, etc",
                "phone": "+91-9999999999"
            },
            "fulfillments": [
                {
                    "state": {
                        "descriptor": {
                            "code": "APPLICATION-STARTED",
                            "name": "Application started"
                        },
                        "updated_at": "2023-02-06T09:55:41.161Z"
                    },
                    "id": "VSP_FUL_1113",
                    "tracking": false,
                    "agent": {
                        "person": {
                            "name": "Ekstep Foundation SPoc"
                        },
                        "contact": {
                            "email": "ekstepsupport@ekstep.com"
                        }
                    },
                    "customer": {
                        "id": "aadhaar:798677675565",
                        "person": {
                            "name": "Jane Doe",
                            "age": "13",
                            "gender": "female"
                        },
                        "contact": {
                            "phone": "+91-9663088848",
                            "email": "jane.doe@example.com"
                        }
                    }
                }
            ],
            "payments": [
                {
                    "params": {
                        "bank_code": "IFSC_Code_Of_the_bank",
                        "bank_account_number": "121212121212",
                        "bank_account_name": "Account Holder Name"
                    }
                }
            ],
            "quote": {
                "price": {
                    "currency": "INR",
                    "value": "250000"
                },
                "breakup": [
                    {
                        "title": "Tution fee",
                        "price": {
                            "currency": "INR",
                            "value": "150000"
                        }
                    },
                    {
                        "title": "Hostel fee",
                        "price": {
                            "currency": "INR",
                            "value": "50000"
                        }
                    },
                    {
                        "title": "Books",
                        "price": {
                            "currency": "INR",
                            "value": "50000"
                        }
                    }
                ]
            }
        }
    }
}
```

Here the BPP sends the first form to be filled. Value of `Fulfillment.state.descriptor.code` will be `APPLICATION-STARTED.`

</details>

<details>

<summary>On Init API - Step 2 (post 1st form submission)</summary>

```json
{
    "context": {
        "domain": "onest:financial-support",
        "action": "on_init",
        "timestamvp": "2023-08-02T07:21:58.448Z",
        "ttl": "PT10M",
        "version": "1.1.0",
        "bap_id": "sample.bap.io",
        "bap_uri": "https://sample.bap.io",
        "bpp_id": "sample.bpp.io",
        "bpp_uri": "https://sample.bpp.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
        "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
    },
    "message": {
        "order": {
            "provider": {
                "id": "471",
                "descriptor": {
                    "name": "XYZ Education Foundation",
                    "short_desc": "Short Description about the Foundation",
                    "images": [
                        {
                            "url": "url of the image of the provider"
                        }
                    ]
                },
                "locations": [
                    {
                        "id": "L1",
                        "city": {
                            "name": "Pune",
                            "code": "std:020"
                        },
                        "state": {
                            "name": "Maharastra",
                            "code": "MH"
                        }
                    },
                    {
                        "id": "L2",
                        "city": {
                            "name": "Thane",
                            "code": "std:022"
                        },
                        "state": {
                            "name": "Maharastra",
                            "code": "MH"
                        }
                    }
                ],
                "rateable": false
            },
            "items": [
                {
                    "id": "SCM_63587501",
                    "descriptor": {
                        "name": "XYZ Education Scholarship for Undergraduate Students",
                        "long_desc": "XYZ Education Scholarship for Undergraduate Students"
                    },
                    "price": {
                        "currency": "INR",
                        "value": "1000"
                    },
                    "time": {
                        "range": {
                            "start": "2023-01-03T13:23:01+00:00",
                            "end": "2023-02-03T13:23:01+00:00"
                        }
                    },
                    "xinput": {
                        "required": true,
                        "head": {
                            "descriptor": {
                                "name": "Application Form"
                            },
                            "index": {
                                "min": 0,
                                "cur": 1,
                                "max": 3
                            },
                            "headings": [
                                "Personal Details",
                                "Educational Details",
                                "Financial Information",
                                "Review & Submit"
                            ]
                        },
                        "form": {
                            "mime_type": "text/html",
                            "url": "https://6vs8xnx5i7.vidyasaarathi.co.in/loans-kyc/xinput/formid/a23f2fdfbbb8ac402bfd54f",
                            "resubmit": false,
                            "auth": {
                                "descriptor": {
                                    "code": "jwt"
                                },
                                "value": "eyJhbGciOiJIUzI.eyJzdWIiOiIxMjM0NTY3O.SflKxwRJSMeKKF2QT4"
                            }
                        }
                    },
                    "rateable": false,
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
                                    "value": "In-Progress",
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
                                        "code": "optional-doc",
                                        "name": "Optional document"
                                    },
                                    "value": "PAN No/Domicile certificate",
                                    "display": true
                                }
                            ]
                        },
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
                    ],
                    "location_ids": [
                        "L1",
                        "L2"
                    ],
                    "fulfillment_ids": [
                        "VSP_FUL_1113"
                    ]
                }
            ],
            "billing": {
                "name": "Manjunath",
                "organization": {
                    "descriptor": {
                        "name": "Namma Yatri",
                        "code": "nammayatri.in"
                    },
                    "contact": {
                        "phone": "+91-8888888888",
                        "email": "scholarships@nammayatri.in"
                    }
                },
                "address": "No 27, XYZ Lane, etc",
                "phone": "+91-9999999999"
            },
            "fulfillments": [
                {
                    "state": {
                        "descriptor": {
                            "code": "APPLICATION-IN-PROGRESS",
                            "name": "Application In Progress"
                        },
                        "updated_at": "2023-02-06T09:55:41.161Z"
                    },
                    "id": "VSP_FUL_1113",
                    "tracking": false,
                    "agent": {
                        "person": {
                            "name": "Ekstep Foundation SPoc"
                        },
                        "contact": {
                            "email": "ekstepsupport@ekstep.com"
                        }
                    },
                    "customer": {
                        "id": "aadhaar:798677675565",
                        "person": {
                            "name": "Jane Doe",
                            "age": "13",
                            "gender": "female"
                        },
                        "contact": {
                            "phone": "+91-9663088848",
                            "email": "jane.doe@example.com"
                        }
                    }
                }
            ],
            "payments": [
                {
                    "params": {
                        "bank_code": "IFSC_Code_Of_the_bank",
                        "bank_account_number": "121212121212",
                        "bank_account_name": "Account Holder Name"
                    }
                }
            ],
            "quote": {
                "price": {
                    "currency": "INR",
                    "value": "250000"
                },
                "breakup": [
                    {
                        "title": "Tution fee",
                        "price": {
                            "currency": "INR",
                            "value": "150000"
                        }
                    },
                    {
                        "title": "Hostel fee",
                        "price": {
                            "currency": "INR",
                            "value": "50000"
                        }
                    },
                    {
                        "title": "Books",
                        "price": {
                            "currency": "INR",
                            "value": "50000"
                        }
                    }
                ]
            }
        }
    }
}
```

Here fulfillment status will be `APPLICATION-IN-PROGRESS` as the user has already submitted the first form and the second form is sent by the BPP in this API.

</details>

<details>

<summary>On Init API - Step 3 (post 2nd form submission)</summary>

```json
{
    "context": {
        "domain": "onest:financial-support",
        "action": "on_init",
        "timestamp": "2023-08-02T07:21:58.448Z",
        "ttl": "PT10M",
        "version": "1.1.0",
        "bap_id": "sample.bap.io",
        "bap_uri": "https://sample.bap.io",
        "bpp_id": "sample.bpp.io",
        "bpp_uri": "https://sample.bpp.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
        "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
    },
    "message": {
        "order": {
            "provider": {
                "id": "471",
                "descriptor": {
                    "name": "XYZ Education Foundation",
                    "short_desc": "Short Description about the Foundation",
                    "images": [
                        {
                            "url": "url of the image of the provider"
                        }
                    ]
                },
                "locations": [
                    {
                        "id": "L1",
                        "city": {
                            "name": "Pune",
                            "code": "std:020"
                        },
                        "state": {
                            "name": "Maharastra",
                            "code": "MH"
                        }
                    },
                    {
                        "id": "L2",
                        "city": {
                            "name": "Thane",
                            "code": "std:022"
                        },
                        "state": {
                            "name": "Maharastra",
                            "code": "MH"
                        }
                    }
                ],
                "rateable": false
            },
            "items": [
                {
                    "id": "SCM_63587501",
                    "descriptor": {
                        "name": "XYZ Education Scholarship for Undergraduate Students",
                        "long_desc": "XYZ Education Scholarship for Undergraduate Students"
                    },
                    "price": {
                        "currency": "INR",
                        "value": "1000"
                    },
                    "time": {
                        "range": {
                            "start": "2023-01-03T13:23:01+00:00",
                            "end": "2023-02-03T13:23:01+00:00"
                        }
                    },
                    "xinput": {
                        "required": true,
                        "head": {
                            "descriptor": {
                                "name": "Application Form"
                            },
                            "index": {
                                "min": 0,
                                "cur": 2,
                                "max": 3
                            },
                            "headings": [
                                "Personal Details",
                                "Educational Details",
                                "Financial Information",
                                "Review & Submit"
                            ]
                        },
                        "form": {
                            "mime_type": "text/html",
                            "url": "https://6vs8xnx5i7.vidyasaarathi.co.in/loans-kyc/xinput/formid/a23f2fdfbbb8ac402bfd54f",
                            "resubmit": false,
                            "auth": {
                                "descriptor": {
                                    "code": "jwt"
                                },
                                "value": "eyJhbGciOiJIUzI.eyJzdWIiOiIxMjM0NTY3O.SflKxwRJSMeKKF2QT4"
                            }
                        }
                    },
                    "rateable": false,
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
                                    "value": "In-Progress",
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
                                        "code": "optional-doc",
                                        "name": "Optional document"
                                    },
                                    "value": "PAN No/Domicile certificate",
                                    "display": true
                                }
                            ]
                        },
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
                                        "short_desc": "Link to FAQ"
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
                    ],
                    "location_ids": [
                        "L1",
                        "L2"
                    ],
                    "fulfillment_ids": [
                        "VSP_FUL_1113"
                    ]
                }
            ],
            "billing": {
                "name": "Manjunath",
                "organization": {
                    "descriptor": {
                        "name": "Namma Yatri",
                        "code": "nammayatri.in"
                    },
                    "contact": {
                        "phone": "+91-8888888888",
                        "email": "scholarships@nammayatri.in"
                    }
                },
                "address": "No 27, XYZ Lane, etc",
                "phone": "+91-9999999999"
            },
            "fulfillments": [
                {
                    "state": {
                        "descriptor": {
                            "code": "APPLICATION-IN-PROGRESS",
                            "name": "Application In Progress"
                        },
                        "updated_at": "2023-02-06T09:55:41.161Z"
                    },
                    "id": "VSP_FUL_1113",
                    "tracking": false,
                    "agent": {
                        "person": {
                            "name": "Ekstep Foundation SPoc"
                        },
                        "contact": {
                            "email": "ekstepsupport@ekstep.com"
                        }
                    },
                    "customer": {
                        "id": "aadhaar:798677675565",
                        "person": {
                            "name": "Jane Doe",
                            "age": "13",
                            "gender": "female"
                        },
                        "contact": {
                            "phone": "+91-9663088848",
                            "email": "jane.doe@example.com"
                        }
                    }
                }
            ],
            "payments": [
                {
                    "params": {
                        "bank_code": "IFSC_Code_Of_the_bank",
                        "bank_account_number": "121212121212",
                        "bank_account_name": "Account Holder Name"
                    }
                }
            ],
            "quote": {
                "price": {
                    "currency": "INR",
                    "value": "250000"
                },
                "breakup": [
                    {
                        "title": "Tution fee",
                        "price": {
                            "currency": "INR",
                            "value": "150000"
                        }
                    },
                    {
                        "title": "Hostel fee",
                        "price": {
                            "currency": "INR",
                            "value": "50000"
                        }
                    },
                    {
                        "title": "Books",
                        "price": {
                            "currency": "INR",
                            "value": "50000"
                        }
                    }
                ]
            }
        }
    }
}
```

</details>

<details>

<summary>On Init API - Step 4 (post 3rd form submission)</summary>

```json
{
    "context": {
        "domain": "onest:financial-support",
        "action": "on_init",
        "timestamp": "2023-08-02T07:21:58.448Z",
        "ttl": "PT10M",
        "version": "1.1.0",
        "bap_id": "sample.bap.io",
        "bap_uri": "https://sample.bap.io",
        "bpp_id": "sample.bpp.io",
        "bpp_uri": "https://sample.bpp.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
        "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
    },
    "message": {
        "order": {
            "provider": {
                "id": "471",
                "descriptor": {
                    "name": "XYZ Education Foundation",
                    "short_desc": "Short Description about the Foundation",
                    "images": [
                        {
                            "url": "url of the image of the provider"
                        }
                    ]
                },
                "locations": [
                    {
                        "id": "L1",
                        "city": {
                            "name": "Pune",
                            "code": "std:020"
                        },
                        "state": {
                            "name": "Maharastra",
                            "code": "MH"
                        }
                    },
                    {
                        "id": "L2",
                        "city": {
                            "name": "Thane",
                            "code": "std:022"
                        },
                        "state": {
                            "name": "Maharastra",
                            "code": "MH"
                        }
                    }
                ],
                "rateable": false
            },
            "items": [
                {
                    "id": "SCM_63587501",
                    "descriptor": {
                        "name": "XYZ Education Scholarship for Undergraduate Students",
                        "long_desc": "XYZ Education Scholarship for Undergraduate Students"
                    },
                    "price": {
                        "currency": "INR",
                        "value": "1000"
                    },
                    "time": {
                        "range": {
                            "start": "2023-01-03T13:23:01+00:00",
                            "end": "2023-02-03T13:23:01+00:00"
                        }
                    },
                    "xinput": {
                        "required": true,
                        "head": {
                            "descriptor": {
                                "name": "Application Form"
                            },
                            "index": {
                                "min": 0,
                                "cur": 3,
                                "max": 3
                            },
                            "headings": [
                                "Personal Details",
                                "Educational Details",
                                "Financial Information",
                                "Review & Submit"
                            ]
                        },
                        "form": {
                            "mime_type": "text/html",
                            "url": "https://6vs8xnx5i7.vidyasaarathi.co.in/loans-kyc/xinput/formid/a23f2fdfbbb8ac402bfd54f",
                            "resubmit": false,
                            "auth": {
                                "descriptor": {
                                    "code": "jwt"
                                },
                                "value": "eyJhbGciOiJIUzI.eyJzdWIiOiIxMjM0NTY3O.SflKxwRJSMeKKF2QT4"
                            }
                        }
                    },
                    "rateable": false,
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
                                    "value": "In-Progress",
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
                                        "code": "optional-doc",
                                        "name": "Optional document"
                                    },
                                    "value": "PAN No/Domicile certificate",
                                    "display": true
                                }
                            ]
                        },
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
                                        "short_desc": "Link to FAQ"
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
                    ],
                    "location_ids": [
                        "L1",
                        "L2"
                    ],
                    "fulfillment_ids": [
                        "VSP_FUL_1113"
                    ]
                }
            ],
            "billing": {
                "name": "Manjunath",
                "organization": {
                    "descriptor": {
                        "name": "Namma Yatri",
                        "code": "nammayatri.in"
                    },
                    "contact": {
                        "phone": "+91-8888888888",
                        "email": "scholarships@nammayatri.in"
                    }
                },
                "address": "No 27, XYZ Lane, etc",
                "phone": "+91-9999999999"
            },
            "fulfillments": [
                {
                    "state": {
                        "descriptor": {
                            "code": "APPLICATION-IN-PROGRESS",
                            "name": "Application In Progress"
                        },
                        "updated_at": "2023-02-06T09:55:41.161Z"
                    },
                    "id": "VSP_FUL_1113",
                    "tracking": false,
                    "agent": {
                        "person": {
                            "name": "Ekstep Foundation SPoc"
                        },
                        "contact": {
                            "email": "ekstepsupport@ekstep.com"
                        }
                    },
                    "customer": {
                        "id": "aadhaar:798677675565",
                        "person": {
                            "name": "Jane Doe",
                            "age": "13",
                            "gender": "female"
                        },
                        "contact": {
                            "phone": "+91-9663088848",
                            "email": "jane.doe@example.com"
                        }
                    }
                }
            ],
            "payments": [
                {
                    "params": {
                        "bank_code": "IFSC_Code_Of_the_bank",
                        "bank_account_number": "121212121212",
                        "bank_account_name": "Account Holder Name"
                    }
                }
            ],
            "quote": {
                "price": {
                    "currency": "INR",
                    "value": "250000"
                },
                "breakup": [
                    {
                        "title": "Tution fee",
                        "price": {
                            "currency": "INR",
                            "value": "150000"
                        }
                    },
                    {
                        "title": "Hostel fee",
                        "price": {
                            "currency": "INR",
                            "value": "50000"
                        }
                    },
                    {
                        "title": "Books",
                        "price": {
                            "currency": "INR",
                            "value": "50000"
                        }
                    }
                ]
            }
        }
    }
}
```

</details>

<details>

<summary>On Init API - Step 5 (post last form submission)</summary>

If there are no more forms to be filled, BPP will send on\_init request without xinput form details. Fulfillment status will be `APPLICATION-FILLED`.

```json
{
    "context": {
        "domain": "onest:financial-support",
        "location": {
            "city": {
                "name": "Bangalore",
                "code": "std:080"
            },
            "country": {
                "name": "India",
                "code": "IND"
            }
        },
        "action": "on_init",
        "timestamp": "2023-08-02T07:21:58.448Z",
        "ttl": "PT10M",
        "version": "1.1.0",
        "bap_id": "sample.bap.io",
        "bap_uri": "https://sample.bap.io",
        "bpp_id": "sample.bpp.io",
        "bpp_uri": "https://sample.bpp.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
        "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
    },
    "message": {
        "order": {
            "provider": {
                "id": "471",
                "descriptor": {
                    "name": "XYZ Education Foundation",
                    "short_desc": "Short Description about the Foundation",
                    "images": [
                        {
                            "url": "url of the image of the provider"
                        }
                    ]
                },
                "locations": [
                    {
                        "id": "L1",
                        "city": {
                            "name": "Pune",
                            "code": "std:020"
                        },
                        "state": {
                            "name": "Maharastra",
                            "code": "MH"
                        }
                    },
                    {
                        "id": "L2",
                        "city": {
                            "name": "Thane",
                            "code": "std:022"
                        },
                        "state": {
                            "name": "Maharastra",
                            "code": "MH"
                        }
                    }
                ],
                "rateable": false
            },
            "items": [
                {
                    "id": "SCM_63587501",
                    "descriptor": {
                        "name": "XYZ Education Scholarship for Undergraduate Students",
                        "long_desc": "XYZ Education Scholarship for Undergraduate Students"
                    },
                    "price": {
                        "currency": "INR",
                        "value": "1000"
                    },
                    "time": {
                        "range": {
                            "start": "2023-01-03T13:23:01+00:00",
                            "end": "2023-02-03T13:23:01+00:00"
                        }
                    },
                    "rateable": false,
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
                                    "value": "In-Progress",
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
                                        "code": "optional-doc",
                                        "name": "Optional document"
                                    },
                                    "value": "PAN No/Domicile certificate",
                                    "display": true
                                }
                            ]
                        },
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
                                        "short_desc": "Link to FAQ"
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
                    ],
                    "location_ids": [
                        "L1",
                        "L2"
                    ],
                    "fulfillment_ids": [
                        "VSP_FUL_1113"
                    ]
                }
            ],
            "billing": {
                "name": "Manjunath",
                "organization": {
                    "descriptor": {
                        "name": "Namma Yatri",
                        "code": "nammayatri.in"
                    },
                    "contact": {
                        "phone": "+91-8888888888",
                        "email": "scholarships@nammayatri.in"
                    }
                },
                "address": "No 27, XYZ Lane, etc",
                "phone": "+91-9999999999"
            },
            "fulfillments": [
                {
                    "state": {
                        "descriptor": {
                            "code": "APPLICATION-FILLED",
                            "name": "Application Filled"
                        },
                        "updated_at": "2023-02-06T09:55:41.161Z"
                    },
                    "id": "VSP_FUL_1113",
                    "tracking": false,
                    "agent": {
                        "person": {
                            "name": "Ekstep Foundation SPoc"
                        },
                        "contact": {
                            "email": "ekstepsupport@ekstep.com"
                        }
                    },
                    "customer": {
                        "id": "aadhaar:798677675565",
                        "person": {
                            "name": "Jane Doe",
                            "age": "13",
                            "gender": "female"
                        },
                        "contact": {
                            "phone": "+91-9663088848",
                            "email": "jane.doe@example.com"
                        }
                    }
                }
            ],
            "payments": [
                {
                    "params": {
                        "bank_code": "IFSC_Code_Of_the_bank",
                        "bank_account_number": "121212121212",
                        "bank_account_name": "Account Holder Name"
                    }
                }
            ],
            "quote": {
                "price": {
                    "currency": "INR",
                    "value": "250000"
                },
                "breakup": [
                    {
                        "title": "Tution fee",
                        "price": {
                            "currency": "INR",
                            "value": "150000"
                        }
                    },
                    {
                        "title": "Hostel fee",
                        "price": {
                            "currency": "INR",
                            "value": "50000"
                        }
                    },
                    {
                        "title": "Books",
                        "price": {
                            "currency": "INR",
                            "value": "50000"
                        }
                    }
                ]
            }
        }
    }
}
```

</details>

5. BAP sends confirms request to confirm the scholarship application.\
   \
   Distributor details(tag) and fields in it are optional. These details are collected by seeker and sent to provider.

<details>

<summary>Confirm API</summary>

```json
{
  "context": {
    "domain": "onest:financial-support",
    "location": {
      "city": {
        "name": "Bangalore",
        "code": "std:080"
      },
      "country": {
        "name": "India",
        "code": "IND"
      }
    },
    "action": "confirm",
    "timestamp": "2023-08-02T07:21:58.448Z",
    "ttl": "PT10M",
    "version": "1.1.0",
    "bap_id": "sample.bap.io",
    "bap_uri": "https://sample.bap.io",
    "bpp_id": "sample.bpp.io",
    "bpp_uri": "https://sample.bpp.io",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
    "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
  },
  "message": {
    "order": {
      "items": [
        {
          "id": "SCM_63587501"
        }
      ],
      "provider": {
        "id": "BX213573733"
      },
      "billing": {
        "name": "Manjunath",
        "organization": {
          "descriptor": {
            "name": "Namma Yatri",
            "code": "nammayatri.in"
          },
          "contact": {
            "phone": "+91-8888888888",
            "email": "scholarships@nammayatri.in"
          }
        },
        "address": "No 27, XYZ Lane, etc",
        "phone": "+91-9999999999"
      },
      "fulfillments": [
        {
          "customer": {
            "id": "aadhaar:798677675565",
            "person": {
              "name": "Jane Doe",
              "age": "13",
              "gender": "female"
            },
            "contact": {
              "phone": "+91-9663088848",
              "email": "jane.doe@example.com"
            }
          },
          "tags": [
            {
              "code": "distributor-details",
              "list": [
                {
                  "descriptor": {
                    "code": "distributor-id",
                    "name": "Distributor Id"
                  },
                  "value": "PNB"
                },
                {
                  "descriptor": {
                    "code": "distributor-name",
                    "name": "Distributor Name"
                  },
                  "value": "Pay Near By"
                },
                {
                  "descriptor": {
                    "code": "distributor-phone",
                    "name": "Distributor Phone"
                  },
                  "value": "9123456789"
                },
                {
                  "descriptor": {
                    "code": "distributor-email",
                    "name": "Distributor Email"
                  },
                  "value": "support@pnb.com"
                },
                {
                  "descriptor": {
                    "code": "agent-id",
                    "name": "Agent Id"
                  },
                  "value": "agent-123"
                },
                {
                  "descriptor": {
                    "code": "agent-verified",
                    "name": "Agent verified"
                  },
                  "value": "true"
                }
              ]
            }
          ]
        }
      ],
      "payment": [
        {
          "params": {
            "bank_code": "IFSC_Code_Of_the_bank",
            "bank_account_number": "121212121212",
            "bank_account_name": "Account Holder Name"
          }
        }
      ]
    }
  }
}
```

</details>

6. BPP will send the confirmation of submission of the scholarship application.

<details>

<summary>On Confirm API</summary>

```json
{
    "context": {
       "domain": "onest:financial-support",
       "action": "on_confirm",
       "timestamp": "2023-08-02T07:21:58.448Z",
       "ttl": "PT10M",
       "version": "1.1.0",
       "bap_id": "sample.bap.io",
       "bap_uri": "https://sample.bap.io",
       "bpp_id": "sample.bpp.io",
       "bpp_uri": "https://sample.bpp.io",
       "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
       "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
    },
    "message": {
       "order": {
          "id": "12424kh",
          "provider": {
             "id": "471",
             "descriptor": {
                "name": "XYZ Education Foundation",
                "short_desc" : "Short Description about the Foundation",
                "images": [
                   {
                      "url" : "https://xyz.com/logo"
                   }
                ]
             },
             "locations": [
                {
                    "id": "L1",
                    "city": {
                        "name": "Pune",
                        "code": "std:020"
                    },
                    "state": {
                        "name": "Maharastra",
                        "code": "MH"
                    }
                },
                {
                    "id": "L2",
                    "city": {
                        "name": "Thane",
                        "code": "std:022"
                    },
                    "state": {
                        "name": "Maharastra",
                        "code": "MH"
                    }
                }
            ],
             "rateable": false
          },
          "items": [
             {
                "id": "SCM_63587501",
                "descriptor": {
                   "name": "XYZ Education Scholarship for Undergraduate Students",
                   "long_desc": "XYZ Education Scholarship for Undergraduate Students"
                },
                "price": {
                   "currency": "INR",
                   "value": "1000"
                },
                "time": {
                        "range": {
                            "start": "2023-01-03T13:23:01+00:00",
                            "end": "2023-02-03T13:23:01+00:00"
                        }
                    },
                "rateable": false,
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
                                "value": "In-Progress",
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
                                    "code": "optional-doc",
                                    "name": "Optional document"
                                },
                                "value": "PAN No/Domicile certificate",
                                "display": true
                            }
                        ]
                    },
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
                                    "short_desc": "Link to FAQ"
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
                ],
                "location_ids": [
                    "L1",
                    "L2"
                ],
                "fulfillment_ids": [
                   "VSP_FUL_1113"
                ]
             }
          ],
          "billing": {
             "name": "Manjunath",
             "organization": {
                "descriptor": {
                   "name": "Namma Yatri",
                   "code": "nammayatri.in"
                },
                "contact": {
                   "phone": "+91-8888888888",
                   "email": "scholarships@nammayatri.in"
                }
             },
             "address": "No 27, XYZ Lane, etc",
             "phone": "+91-9999999999"
          },
          "fulfillments": [
             {
                "state" : {
                   "descriptor" : {
                      "code": "APPLICATION-SUBMITTED",
                      "name" : "Application Submitted"
                   },
                   "updated_at" : "2023-02-06T09:55:41.161Z"
                },
                "id": "VSP_FUL_1113",
                "tracking": false,
                "agent" : {
                   "person" : {
                      "name" : "Ekstep Foundation SPoc"
                   },
                   "contact" : {
                      "email" : "ekstepsupport@ekstep.com"
                   }
                },
                "customer": {
                   "id": "aadhaar:798677675565",
                   "person": {
                      "name": "Jane Doe",
                      "age": "13",
                      "gender": "female"
                   },
                   "contact": {
                      "phone": "+91-9663088848",
                      "email": "jane.doe@example.com"
                   }
                }
             }
          ],
          "payments" : [
             {
                "params" :{
                   "bank_code": "IFSC_Code_Of_the_bank",
                   "bank_account_number" :"121212121212",
                   "bank_account_name" : "Account Holder Name"
                }
 
             }
          ],
          "quote" :{
             "price" : {
                "currency" : "INR",
                "value" : "250000"
             },
             "breakup":[
                {
                   "title": "Tution fee",
                   "price" : {
                      "currency" : "INR",
                      "value" : "150000"
                   }
                },
                {
                   "title": "Hostel fee",
                   "price" : {
                      "currency" : "INR",
                      "value" : "50000"
                   }
                },
                {
                   "title": "Books",
                   "price" : {
                      "currency" : "INR",
                      "value" : "50000"
                   }
                }
             ]
          }
       }
    }
 }
```

</details>

7. BAP can use the status API to fetch the scholarship application status.

<details>

<summary>Status API</summary>

```json
{
   "context": {
      "domain": "onest:financial-support",
      "action": "status",
      "timestamp": "2023-08-02T07:21:58.448Z",
      "ttl": "PT10M",
      "version": "1.1.0",
      "bap_id": "sample.bap.io",
      "bap_uri": "https://sample.bap.io",
      "bpp_id": "sample.bpp.io",
      "bpp_uri": "https://sample.bpp.io",
      "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
      "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
   },
    "message": {
        "order_id" : "12424kh"
    }
}
```

</details>

8. BPP send the on\_status request, with scholarship application status. On any status change to the application, the BPP can send the on\_status request with the updated order object unsolicited to the BAP. The BPP will use the same transaction ID as the order and generate a new message ID.

<details>

<summary>On Status - Application Approved</summary>

```json
{
    "context": {
        "domain": "onest:financial-support",
        "action": "on_status",
        "timestamp": "2023-08-02T07:21:58.448Z",
        "ttl": "PT10M",
        "version": "1.1.0",
        "bap_id": "sample.bap.io",
        "bap_uri": "https://sample.bap.io",
        "bpp_id": "sample.bpp.io",
        "bpp_uri": "https://sample.bpp.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
        "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
    },
    "message": {
        "order": {
            "id": "12424kh",
            "provider": {
                "id": "471",
                "descriptor": {
                    "name": "XYZ Education Foundation",
                    "short_desc": "Short Description about the Foundation",
                    "images": [
                        {
                            "url": "url of the image of the provider"
                        }
                    ]
                },
                "rateable": false
            },
            "items": [
                {
                    "id": "SCM_63587501",
                    "descriptor": {
                        "name": "XYZ Education Scholarship for Undergraduate Students",
                        "long_desc": "XYZ Education Scholarship for Undergraduate Students"
                    },
                    "price": {
                        "currency": "INR",
                        "value": "1000"
                    },
                    "time": {
                        "range": {
                            "start": "2023-01-03T13:23:01+00:00",
                            "end": "2023-02-03T13:23:01+00:00"
                        }
                    },
                    "rateable": false,
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
                                    "value": "In-Progress",
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
                                        "code": "optional-doc",
                                        "name": "Optional document"
                                    },
                                    "value": "PAN No/Domicile certificate",
                                    "display": true
                                }
                            ]
                        },
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
                                        "short_desc": "Link to FAQ"
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
                    ],
                    "fulfillment_ids": [
                        "VSP_FUL_1113"
                    ]
                }
            ],
            "billing": {
                "name": "Manjunath",
                "organization": {
                    "descriptor": {
                        "name": "Namma Yatri",
                        "code": "nammayatri.in"
                    },
                    "contact": {
                        "phone": "+91-8888888888",
                        "email": "scholarships@nammayatri.in"
                    }
                },
                "address": "No 27, XYZ Lane, etc",
                "phone": "+91-9999999999"
            },
            "fulfillments": [
                {
                    "state": {
                        "descriptor": {
                            "code": "APPLICATION-APPROVED",
                            "name": "Application Approved"
                        },
                        "updated_at": "2023-02-06T09:55:41.161Z"
                    },
                    "id": "VSP_FUL_1113",
                    "type": "SCHOLARSHIP",
                    "tracking": false,
                    "agent": {
                        "person": {
                            "name": "Ekstep Foundation SPoc"
                        },
                        "contact": {
                            "email": "ekstepsupport@ekstep.com"
                        }
                    },
                    "customer": {
                        "id": "aadhaar:798677675565",
                        "person": {
                            "name": "Jane Doe",
                            "age": "13",
                            "gender": "female"
                        },
                        "contact": {
                            "phone": "+91-9663088848",
                            "email": "jane.doe@example.com"
                        }
                    }
                }
            ],
            "payments": [
                {
                    "params": {
                        "bank_code": "IFSC_Code_Of_the_bank",
                        "bank_account_number": "121212121212",
                        "bank_account_name": "Account Holder Name"
                    }
                }
            ],
            "quote": {
                "price": {
                    "currency": "INR",
                    "value": "250000"
                },
                "breakup": [
                    {
                        "title": "Tution fee",
                        "price": {
                            "currency": "INR",
                            "value": "150000"
                        }
                    },
                    {
                        "title": "Hostel fee",
                        "price": {
                            "currency": "INR",
                            "value": "50000"
                        }
                    },
                    {
                        "title": "Books",
                        "price": {
                            "currency": "INR",
                            "value": "50000"
                        }
                    }
                ]
            }
        }
    }
}
```

</details>

<details>

<summary>On Status - Application Rejected</summary>

```json
{
    "context": {
        "domain": "onest:financial-support",
        "action": "on_status",
        "timestamp": "2023-08-02T07:21:58.448Z",
        "ttl": "PT10M",
        "version": "1.1.0",
        "bap_id": "sample.bap.io",
        "bap_uri": "https://sample.bap.io",
        "bpp_id": "sample.bpp.io",
        "bpp_uri": "https://sample.bpp.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c60008",
        "message_id": "f6a7d7ea-a23e-4419-b07e-a3412fdffecf"
    },
    "message": {
        "order": {
            "id": "12424kh",
            "provider": {
                "id": "471",
                "descriptor": {
                    "name": "XYZ Education Foundation",
                    "short_desc": "Short Description about the Foundation",
                    "images": [
                        {
                            "url": "url of the image of the provider"
                        }
                    ]
                },
                "rateable": false
            },
            "items": [
                {
                    "id": "SCM_63587501",
                    "descriptor": {
                        "name": "XYZ Education Scholarship for Undergraduate Students",
                        "long_desc": "XYZ Education Scholarship for Undergraduate Students"
                    },
                    "price": {
                        "currency": "INR",
                        "value": "1000"
                    },
                    "time": {
                        "range": {
                            "start": "2023-01-03T13:23:01+00:00",
                            "end": "2023-02-03T13:23:01+00:00"
                        }
                    },
                    "rateable": false,
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
                                    "value": "In-Progress",
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
                                        "code": "optional-doc",
                                        "name": "Optional document"
                                    },
                                    "value": "PAN No/Domicile certificate",
                                    "display": true
                                }
                            ]
                        },
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
                                        "short_desc": "Link to FAQ"
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
                    ],
                    "fulfillment_ids": [
                        "VSP_FUL_1113"
                    ]
                }
            ],
            "billing": {
                "name": "Manjunath",
                "organization": {
                    "descriptor": {
                        "name": "Namma Yatri",
                        "code": "nammayatri.in"
                    },
                    "contact": {
                        "phone": "+91-8888888888",
                        "email": "scholarships@nammayatri.in"
                    }
                },
                "address": "No 27, XYZ Lane, etc",
                "phone": "+91-9999999999"
            },
            "fulfillments": [
                {
                    "state": {
                        "descriptor": {
                            "code": "APPLICATION-REJECTED",
                            "name": "Application Rejected"
                        },
                        "updated_at": "2023-02-06T09:55:41.161Z"
                    },
                    "id": "VSP_FUL_1113",
                    "type": "SCHOLARSHIP",
                    "tracking": false,
                    "agent": {
                        "person": {
                            "name": "Ekstep Foundation SPoc"
                        },
                        "contact": {
                            "email": "ekstepsupport@ekstep.com"
                        }
                    },
                    "customer": {
                        "id": "aadhaar:798677675565",
                        "person": {
                            "name": "Jane Doe",
                            "age": "13",
                            "gender": "female"
                        },
                        "contact": {
                            "phone": "+91-9663088848",
                            "email": "jane.doe@example.com"
                        }
                    }
                }
            ],
            "payments": [
                {
                    "params": {
                        "bank_code": "IFSC_Code_Of_the_bank",
                        "bank_account_number": "121212121212",
                        "bank_account_name": "Account Holder Name"
                    }
                }
            ],
            "quote": {
                "price": {
                    "currency": "INR",
                    "value": "250000"
                },
                "breakup": [
                    {
                        "title": "Tution fee",
                        "price": {
                            "currency": "INR",
                            "value": "150000"
                        }
                    },
                    {
                        "title": "Hostel fee",
                        "price": {
                            "currency": "INR",
                            "value": "50000"
                        }
                    },
                    {
                        "title": "Books",
                        "price": {
                            "currency": "INR",
                            "value": "50000"
                        }
                    }
                ]
            }
        }
    }
}
```

</details>

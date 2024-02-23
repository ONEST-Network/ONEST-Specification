# Learning Experience

### Usecase:&#x20;

A provider platform which acts as BPP hosts the courses and a seeker platform which acts as BAP helps the people to find courses.

### Flow Diagram:

<figure><img src="../../assets/learning-experience-flow.jpg" alt=""><figcaption></figcaption></figure>

### API Mapping and Sample JSON's:

1. BAP will make search request with an intent, ex: course name, course provider etc.

#### Search API (Search By Course Name)

```json
{
  "context": {
    "domain": "onest:learning-experiences",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62196",
    "message_id": "$bb579fb8-cb82-4824-be12-fcbc405b6608",
    "action": "search",
    "timestamp": "2022-12-15T05:23:03.443Z",
    "version": "1.1.0",
    "bap_uri": "https://sample.bap.io/",
    "bap_id": "sample.bap.io",
    "ttl": "PT10M"
  },
  "message": {
    "intent": {
      "item": {
        "descriptor": {
          "name": "english"
        }
      }
    }
  }
}
```

2. BPP will create a catalogue of courses with matching criteria and sends it in on\_search request.

#### On Search API&#x20;

The request will contain only minimal details about the job like course name, description, images, preview, price, ratings etc.

```json
{
  "context": {
    "domain": "onest:learning-experiences",
    "version": "1.1.0",
    "action": "on_search",
    "bap_uri": "https://sample.bap.io",
    "bap_id": "sample.bap.io",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62196",
    "message_id": "7db91181-718f-4720-83de-88e36e9f854e",
    "ttl": "PT10M",
    "timestamp": "2023-02-22T10:30:18.145Z",
    "bpp_id": "sample.bpp.io",
    "bpp_uri": "https://sample.bpp.io"
  },
  "message": {
    "catalog": {
      "descriptor": {
        "name": "Catalog for English courses"
      },
      "providers": [
        {
          "id": "INFOSYS",
          "descriptor": {
            "name": "Infosys Springboard",
            "short_desc": "Infosys Springboard Digital literacy program",
            "images": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/app_logos/landing-new.png",
                "size_type": "sm"
              }
            ]
          },
          "categories": [
            {
              "id": "LANGUAGE-COURSES",
              "descriptor": {
                "code": "LANGUAGE-COURSES",
                "name": "Language Courses"
              }
            },
            {
              "id": "SKILL-DEVELOPMENT-COURSES",
              "descriptor": {
                "code": "SKILL-DEVELOPMENT-COURSES",
                "name": "Skill development Courses"
              }
            },
            {
              "id": "TECHNICAL-COURSES",
              "descriptor": {
                "code": "TECHNICAL-COURSES",
                "name": "Technical Courses"
              }
            },
            {
              "id": "SELF-PACED-COURSES",
              "descriptor": {
                "code": "SELF-PACED-COURSES",
                "name": "Self Paced Courses"
              }
            }
          ],
          "items": [
            {
              "id": "d4975df5-b18c-4772-80ad-368669856d52",
              "quantity": {
                "maximum": {
                    "count": 1
                   }
               },
              "descriptor": {
                "name": "Everyday Conversational English",
                "short_desc": "Elevate your daily conversations with confidence through our 'Everyday Conversational English' course.",
                "long_desc": "<p><strong>Course Overview:</strong><br>Welcome to 'Everyday Conversational English,' your key to mastering essential language skills for real-life communication. Tailored for all levels, this course offers:</p><ol><li><strong>Practical Vocabulary:</strong><br>Learn everyday expressions for seamless communication.</li><li><strong>Interactive Role-Playing:</strong><br>Apply knowledge through immersive exercises for real-world scenarios.</li><li><strong>Cultural Insights:</strong><br>Gain cultural nuances to connect authentically in conversations.</li><li><strong>Real-Life Scenarios:</strong><br>Navigate common situations with confidence-building tools.</li><li><strong>Quiz Assessments:</strong><br>Reinforce learning through quizzes for ongoing skill development.</li></ol><p><strong>Why Take This Course:</strong></p><ul><li><strong>Personal & Professional Growth:</strong><br>Enhance personal connections and gain a professional edge.</li><li><strong>Cultural Fluency:</strong><br>Understand and engage with diverse cultures confidently.</li><li><strong>Life-Long Skill:</strong><br>Develop a valuable skill applicable across various life stages.</li></ul><p>Join 'Everyday Conversational English' and elevate your communication for meaningful connections and success.</p>",
                "images": [
                  {
                    "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/everyday-conversational-english.png"
                  }
                ],
                "media": [
                  {
                    "url": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english/preview/"
                  }
                ]
              },
              "creator": {
                "descriptor": {
                  "name": "Prof. Emma Sullivan",
                  "short_desc": "Experienced language educator dedicated to fostering practical conversational skills and cultural fluency",
                  "long_desc": "Hello, I'm Prof. Emma Sullivan, your guide in 'Everyday Conversational English.' With over a decade of experience, I'm here to make language learning dynamic and culturally enriching. Let's explore practical communication skills together for personal and professional growth. Join me on this exciting journey!",
                  "images": [
                    {
                      "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/ins/1.png"
                    }
                  ]
                }
              },
              "price": {
                "currency": "INR",
                "value": "0"
              },
              "category_ids": [
                "LANGUAGE-COURSES",
                "SELF-PACED-COURSES"
              ],
              "rating": "4.5",
              "rateable": true,
              "tags": [
                {
                  "descriptor": {
                    "code": "content-metadata",
                    "name": "Content metadata"
                  },
                  "list": [
                    {
                      "descriptor": {
                        "code": "learner-level",
                        "name": "Learner level"
                      },
                      "value": "Beginner"
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
                        "code": "prerequisite",
                        "name": "Prerequisite"
                      },
                      "value": "Should have a basic understanding of English"
                    },
                    {
                      "descriptor": {
                        "code": "prerequisite",
                        "name": "Prerequisite"
                      },
                      "value": "Access to a computer or internet to access the course online"
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
                  ],
                  "display": true
                }
              ]
            }
          ],
          "fulfillments": [
            {
              "agent": {
                "person": {
                  "name": "Infosys Springboard"
                },
                "contact": {
                  "email": "support@infy.com"
                }
              }
            }
          ]
        }
      ]
    }
  }
}
```

3. BAP will receive the on\_search request and displays the list of courses to the user. Once the user chooses a course, BAP will make select API with item ID to get the complete details about the course.

#### Select API

```json
{
  "context": {
    "domain": "onest:learning-experiences",
    "action": "select",
    "version": "1.1.0",
    "bap_uri": "https://sample.bap.io/",
    "bap_id": "sample.bap.io",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62196",
    "message_id": "$bb579fb8-cb82-4824-be12-fcbc405b6608",
    "timestamp": "2022-12-12T09:55:41.161Z",
    "ttl": "PT10M",
    "bpp_id": "sample.bpp.io",
    "bpp_uri": "https://sample.bpp.io"
  },
  "message": {
    "order": {
      "provider": {
        "id": "INFOSYS"
      },
      "items": [
        {
          "id": "d4975df5-b18c-4772-80ad-368669856d52"
        }
      ]
    }
  }
}
```

4. BPP will receive the select request and check if the course is still valid. If the course is still valid, the BPP will send the on\_select call with complete details of the course.

#### On Select API

```json
{
  "context": {
    "domain": "onest:learning-experiences",
    "version": "1.1.0",
    "action": "on_select",
    "bap_uri": "https://sample.bap.io/",
    "bap_id": "sample.bap.io",
    "bpp_id": "sample.bpp.io",
    "bpp_uri": "https://sample.bpp.io",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62196",
    "message_id": "d514a38f-e112-4bb8-a3d8-b8e5d8dea82d",
    "ttl": "PT10M",
    "timestamp": "2023-02-20T15:21:36.925Z"
  },
  "message": {
    "order": {
      "provider": {
        "id": "INFOSYS",
        "descriptor": {
          "name": "Infosys Springboard",
          "short_desc": "Infosys Springboard Digital literacy program",
          "images": [
            {
              "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/app_logos/landing-new.png",
              "size_type": "sm"
            }
          ]
        },
        "categories": [
          {
            "id": "LANGUAGE-COURSES",
            "descriptor": {
              "code": "LANGUAGE-COURSES",
              "name": "Language Courses"
            }
          },
          {
            "id": "SKILL-DEVELOPMENT-COURSES",
            "descriptor": {
              "code": "SKILL-DEVELOPMENT-COURSES",
              "name": "Skill development Courses"
            }
          },
          {
            "id": "TECHNICAL-COURSES",
            "descriptor": {
              "code": "TECHNICAL-COURSES",
              "name": "Technical Courses"
            }
          },
          {
            "id": "SELF-PACED-COURSES",
            "descriptor": {
              "code": "SELF-PACED-COURSES",
              "name": "Self Paced Courses"
            }
          }
        ]
      },
      "items": [
        {
          "id": "d4975df5-b18c-4772-80ad-368669856d52",
          "quantity": {
            "maximum": {
                    "count": 1
                   }
          },
          "descriptor": {
            "name": "Everyday Conversational English",
            "short_desc": "Elevate your daily conversations with confidence through our 'Everyday Conversational English' course.",
            "long_desc": "<p><strong>Course Overview:</strong><br>Welcome to 'Everyday Conversational English,' your key to mastering essential language skills for real-life communication. Tailored for all levels, this course offers:</p><ol><li><strong>Practical Vocabulary:</strong><br>Learn everyday expressions for seamless communication.</li><li><strong>Interactive Role-Playing:</strong><br>Apply knowledge through immersive exercises for real-world scenarios.</li><li><strong>Cultural Insights:</strong><br>Gain cultural nuances to connect authentically in conversations.</li><li><strong>Real-Life Scenarios:</strong><br>Navigate common situations with confidence-building tools.</li><li><strong>Quiz Assessments:</strong><br>Reinforce learning through quizzes for ongoing skill development.</li></ol><p><strong>Why Take This Course:</strong></p><ul><li><strong>Personal & Professional Growth:</strong><br>Enhance personal connections and gain a professional edge.</li><li><strong>Cultural Fluency:</strong><br>Understand and engage with diverse cultures confidently.</li><li><strong>Life-Long Skill:</strong><br>Develop a valuable skill applicable across various life stages.</li></ul><p>Join 'Everyday Conversational English' and elevate your communication for meaningful connections and success.</p>",
            "images": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/everyday-conversational-english.png"
              }
            ],
            "media": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english/preview/"
              }
            ]
          },
          "creator": {
            "descriptor": {
              "name": "Prof. Emma Sullivan",
              "short_desc": "Experienced language educator dedicated to fostering practical conversational skills and cultural fluency",
              "long_desc": "Hello, I'm Prof. Emma Sullivan, your guide in 'Everyday Conversational English.' With over a decade of experience, I'm here to make language learning dynamic and culturally enriching. Let's explore practical communication skills together for personal and professional growth. Join me on this exciting journey!",
              "images": [
                {
                  "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/ins/1.png"
                }
              ]
            }
          },
          "price": {
            "currency": "INR",
            "value": "150"
          },
          "category_ids": [
            "LANGUAGE-COURSES",
            "SELF-PACED-COURSES"
          ],
          "rating": "4.5",
          "rateable": true,
          "tags": [
            {
              "descriptor": {
                "code": "content-metadata",
                "name": "Content metadata"
              },
              "list": [
                {
                  "descriptor": {
                    "code": "learner-level",
                    "name": "Learner level"
                  },
                  "value": "Beginner"
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
                    "code": "prerequisite",
                    "name": "Prerequisite"
                  },
                  "value": "Should have a basic understanding of English"
                },
                {
                  "descriptor": {
                    "code": "prerequisite",
                    "name": "Prerequisite"
                  },
                  "value": "Access to a computer or internet to access the course online"
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
              ],
              "display": true
            }
          ]
        }
      ],
      "fulfillments": [
        {
          "agent": {
            "person": {
              "name": "Infosys Springboard"
            },
            "contact": {
              "email": "support@infy.com"
            }
          }
        }
      ],
      "quote": {
        "price": {
          "currency": "INR",
          "value": "150"
        }
      }
    }
  }
}

```

5. BAP sends the customer details to the BPP in init API.

#### Init API

```json
{
  "context": {
    "domain": "onest:learning-experiences",
    "action": "init",
    "version": "1.1.0",
    "bap_uri": "https://sample.bap.io/",
    "bap_id": "sample.bap.io",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62196",
    "message_id": "$bb579fb8-cb82-4824-be12-fcbc405b6608",
    "timestamp": "2022-12-12T09:55:41.161Z",
    "ttl": "PT10M",
    "bpp_id": "infosys.springboard.io",
    "bpp_uri": "https://infosys.springboard.io"
  },
  "message": {
    "order": {
      "provider": {
        "id": "INFOSYS"
      },
      "items": [
        {
          "id": "d4975df5-b18c-4772-80ad-368669856d52"
        }
      ],
      "billing": {
        "name": "Jane Doe",
        "phone": "+91-9663088848",
        "email": "jane.doe@example.com",
        "address": "No 27, XYZ Lane, etc"
      },
      "fulfillments": [
        {
          "customer": {
            "person": {
              "name": "Jane Doe",
              "age": "13",
              "gender": "female",
              "tags": [
                {
                  "descriptor": {
                    "code": "professional-details",
                    "name": "Professional Details"
                  },
                  "list": [
                    {
                      "descriptor": {
                        "code": "profession",
                        "name": "profession"
                      },
                      "value": "student"
                    }
                  ],
                  "display": true
                }
              ]
            },
            "contact": {
              "phone": "+91-9663088848",
              "email": "jane.doe@example.com"
            }
          }
        }
      ]
    }
  }
}
```

6. BPP sends the payment URL and if any additional details of the user are required, an xinput form is sent in on\_init request to collect them.\
   \
   If BPP has multiple forms to collect the data, he will make on\_init request with the form number(current index) and total number of forms(max index). BPP should generate the xinput form with transaction id(request.context.transaction\_id). So that the forms can be tagged with a lifecycle.\
   \
   BAP should render the xinput form on the UI and collect all the details.\
   \
   If there are no required xinput forms, the BAP can confirm the order via /confirm API.\
   \
   [Example](https://github.com/beckn/DSEP-Specification/blob/draft/examples/financial-support/forms/scholarship-application-form.html) of xinput form and [recommendation](https://github.com/beckn/protocol-specifications/blob/master/docs/BECKN-007-The-XInput-Schema.md)s to create xinput form.

#### On Init API

```json
{
  "context": {
    "domain": "onest:learning-experiences",
    "version": "1.1.0",
    "action": "on_init",
    "bap_uri": "https://sample.bap.io/",
    "bap_id": "sample.bap.io",
    "bpp_id": "infosys.springboard.io",
    "bpp_uri": "https://infosys.springboard.io",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62196",
    "message_id": "d514a38f-e112-4bb8-a3d8-b8e5d8dea82d",
    "ttl": "PT10M",
    "timestamp": "2023-02-20T15:21:36.925Z"
  },
  "message": {
    "order": {
      "provider": {
        "id": "INFOSYS",
        "descriptor": {
          "name": "Infosys Springboard",
          "short_desc": "Infosys Springboard Digital literacy program",
          "images": [
            {
              "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/app_logos/landing-new.png",
              "size_type": "sm"
            }
          ]
        },
        "categories": [
          {
            "id": "LANGUAGE-COURSES",
            "descriptor": {
              "code": "LANGUAGE-COURSES",
              "name": "Language Courses"
            }
          },
          {
            "id": "SKILL-DEVELOPMENT-COURSES",
            "descriptor": {
              "code": "SKILL-DEVELOPMENT-COURSES",
              "name": "Skill development Courses"
            }
          },
          {
            "id": "TECHNICAL-COURSES",
            "descriptor": {
              "code": "TECHNICAL-COURSES",
              "name": "Technical Courses"
            }
          },
          {
            "id": "SELF-PACED-COURSES",
            "descriptor": {
              "code": "SELF-PACED-COURSES",
              "name": "Self Paced Courses"
            }
          }
        ]
      },
      "items": [
        {
          "id": "d4975df5-b18c-4772-80ad-368669856d52",
          "quantity": {
            "maximum": {
                    "count": 1
                   }
          },
          "descriptor": {
            "name": "Everyday Conversational English",
            "short_desc": "Elevate your daily conversations with confidence through our 'Everyday Conversational English' course.",
            "long_desc": "<p><strong>Course Overview:</strong><br>Welcome to 'Everyday Conversational English,' your key to mastering essential language skills for real-life communication. Tailored for all levels, this course offers:</p><ol><li><strong>Practical Vocabulary:</strong><br>Learn everyday expressions for seamless communication.</li><li><strong>Interactive Role-Playing:</strong><br>Apply knowledge through immersive exercises for real-world scenarios.</li><li><strong>Cultural Insights:</strong><br>Gain cultural nuances to connect authentically in conversations.</li><li><strong>Real-Life Scenarios:</strong><br>Navigate common situations with confidence-building tools.</li><li><strong>Quiz Assessments:</strong><br>Reinforce learning through quizzes for ongoing skill development.</li></ol><p><strong>Why Take This Course:</strong></p><ul><li><strong>Personal & Professional Growth:</strong><br>Enhance personal connections and gain a professional edge.</li><li><strong>Cultural Fluency:</strong><br>Understand and engage with diverse cultures confidently.</li><li><strong>Life-Long Skill:</strong><br>Develop a valuable skill applicable across various life stages.</li></ul><p>Join 'Everyday Conversational English' and elevate your communication for meaningful connections and success.</p>",
            "images": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/everyday-conversational-english.png"
              }
            ],
            "media": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english/preview/"
              }
            ]
          },
          "creator": {
            "descriptor": {
              "name": "Prof. Emma Sullivan",
              "short_desc": "Experienced language educator dedicated to fostering practical conversational skills and cultural fluency",
              "long_desc": "Hello, I'm Prof. Emma Sullivan, your guide in 'Everyday Conversational English.' With over a decade of experience, I'm here to make language learning dynamic and culturally enriching. Let's explore practical communication skills together for personal and professional growth. Join me on this exciting journey!",
              "images": [
                {
                  "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/ins/1.png"
                }
              ]
            }
          },
          "price": {
            "currency": "INR",
            "value": "150"
          },
          "category_ids": [
            "LANGUAGE-COURSES",
            "SELF-PACED-COURSES"
          ],
          "rating": "4.5",
          "rateable": true,
          "xinput": {
            "required": true,
            "head": {
                "descriptor": {
                    "name": "Application Form"
                },
                "index": {
                    "min": 0,
                    "cur": 0,
                    "max": 1
                },
                "headings": [
                    "User Details"
                ]
            },
            "form": {
                "mime_type": "text/html",
                "url": "https://6vs8xnx5i7.co.in/xinput/formid/a23f2fdfbbb8ac402bfd54f-1",
                "resubmit": false
            }
          },
          "tags": [
            {
              "descriptor": {
                "code": "content-metadata",
                "name": "Content metadata"
              },
              "list": [
                {
                  "descriptor": {
                    "code": "learner-level",
                    "name": "Learner level"
                  },
                  "value": "Beginner"
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
                    "code": "prerequisite",
                    "name": "Prerequisite"
                  },
                  "value": "Should have a basic understanding of English"
                },
                {
                  "descriptor": {
                    "code": "prerequisite",
                    "name": "Prerequisite"
                  },
                  "value": "Access to a computer or internet to access the course online"
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
              ],
              "display": true
            }
          ]
        }
      ],
      "fulfillments": [
        {
          "agent": {
            "person": {
              "name": "Infosys Springboard"
            },
            "contact": {
              "email": "support@infy.com"
            }
          },
          "customer": {
            "person": {
              "name": "Jane Doe",
              "age": "13",
              "gender": "female",
              "tags": [
                {
                  "descriptor": {
                    "code": "professional-details",
                    "name": "Professional Details"
                  },
                  "list": [
                    {
                      "descriptor": {
                        "code": "profession",
                        "name": "profession"
                      },
                      "value": "student"
                    }
                  ],
                  "display": true
                }
              ]
            },
            "contact": {
              "phone": "+91-9663088848",
              "email": "jane.doe@example.com"
            }
          }
        }
      ],
      "quote": {
        "price": {
          "currency": "INR",
          "value": "150"
        }
      },
      "billing": {
        "name": "Jane Doe",
        "phone": "+91-9663088848",
        "email": "jane.doe@example.com",
        "address": "No 27, XYZ Lane, etc"
      },
      "payments": [
        {
          "params": {
            "amount": "150",
            "currency": "INR"
          },
          "url": "https://examplepayments.com/pay",
          "type": "PRE-ORDER",
          "status": "NOT-PAID",
          "collected_by": "bpp"
        }
      ]
    }
  }
}
```

7. Using the payment URL, BAP redirects the user to the payment gateway and the user completes the payment. BAP will send one more on\_init with payment status.
   1. If payment is successful, payment.status is PAID.

```json
{
  "context": {
    "domain": "onest:learning-experiences",
    "version": "1.1.0",
    "action": "on_init",
    "bap_uri": "https://sample.bap.io/",
    "bap_id": "sample.bap.io",
    "bpp_id": "sample.bpp.io",
    "bpp_uri": "https://sample.bpp.io",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62196",
    "message_id": "d514a38f-e112-4bb8-a3d8-b8e5d8dea82d",
    "ttl": "PT10M",
    "timestamp": "2023-02-20T15:21:36.925Z"
  },
  "message": {
    "order": {
      "provider": {
        "id": "INFOSYS",
        "descriptor": {
          "name": "Infosys Springboard",
          "short_desc": "Infosys Springboard Digital literacy program",
          "images": [
            {
              "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/app_logos/landing-new.png",
              "size_type": "sm"
            }
          ]
        },
        "categories": [
          {
            "id": "LANGUAGE-COURSES",
            "descriptor": {
              "code": "LANGUAGE-COURSES",
              "name": "Language Courses"
            }
          },
          {
            "id": "SKILL-DEVELOPMENT-COURSES",
            "descriptor": {
              "code": "SKILL-DEVELOPMENT-COURSES",
              "name": "Skill development Courses"
            }
          },
          {
            "id": "TECHNICAL-COURSES",
            "descriptor": {
              "code": "TECHNICAL-COURSES",
              "name": "Technical Courses"
            }
          },
          {
            "id": "SELF-PACED-COURSES",
            "descriptor": {
              "code": "SELF-PACED-COURSES",
              "name": "Self Paced Courses"
            }
          }
        ]
      },
      "items": [
        {
          "id": "d4975df5-b18c-4772-80ad-368669856d52",
          "quantity": {
            "maximum": {
                    "count": 1
                   }
          },
          "descriptor": {
            "name": "Everyday Conversational English",
            "short_desc": "Elevate your daily conversations with confidence through our 'Everyday Conversational English' course.",
            "long_desc": "<p><strong>Course Overview:</strong><br>Welcome to 'Everyday Conversational English,' your key to mastering essential language skills for real-life communication. Tailored for all levels, this course offers:</p><ol><li><strong>Practical Vocabulary:</strong><br>Learn everyday expressions for seamless communication.</li><li><strong>Interactive Role-Playing:</strong><br>Apply knowledge through immersive exercises for real-world scenarios.</li><li><strong>Cultural Insights:</strong><br>Gain cultural nuances to connect authentically in conversations.</li><li><strong>Real-Life Scenarios:</strong><br>Navigate common situations with confidence-building tools.</li><li><strong>Quiz Assessments:</strong><br>Reinforce learning through quizzes for ongoing skill development.</li></ol><p><strong>Why Take This Course:</strong></p><ul><li><strong>Personal & Professional Growth:</strong><br>Enhance personal connections and gain a professional edge.</li><li><strong>Cultural Fluency:</strong><br>Understand and engage with diverse cultures confidently.</li><li><strong>Life-Long Skill:</strong><br>Develop a valuable skill applicable across various life stages.</li></ul><p>Join 'Everyday Conversational English' and elevate your communication for meaningful connections and success.</p>",
            "images": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/everyday-conversational-english.png"
              }
            ],
            "media": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english/preview/"
              }
            ]
          },
          "creator": {
            "descriptor": {
              "name": "Prof. Emma Sullivan",
              "short_desc": "Experienced language educator dedicated to fostering practical conversational skills and cultural fluency",
              "long_desc": "Hello, I'm Prof. Emma Sullivan, your guide in 'Everyday Conversational English.' With over a decade of experience, I'm here to make language learning dynamic and culturally enriching. Let's explore practical communication skills together for personal and professional growth. Join me on this exciting journey!",
              "images": [
                {
                  "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/ins/1.png"
                }
              ]
            }
          },
          "price": {
            "currency": "INR",
            "value": "150"
          },
          "category_ids": [
            "LANGUAGE-COURSES",
            "SELF-PACED-COURSES"
          ],
          "rating": "4.5",
          "rateable": true,
          "tags": [
            {
              "descriptor": {
                "code": "content-metadata",
                "name": "Content metadata"
              },
              "list": [
                {
                  "descriptor": {
                    "code": "learner-level",
                    "name": "Learner level"
                  },
                  "value": "Beginner"
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
                    "code": "prerequisite",
                    "name": "Prerequisite"
                  },
                  "value": "Should have a basic understanding of English"
                },
                {
                  "descriptor": {
                    "code": "prerequisite",
                    "name": "Prerequisite"
                  },
                  "value": "Access to a computer or internet to access the course online"
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
              ],
              "display": true
            }
          ]
        }
      ],
      "fulfillments": [
        {
          "agent": {
            "person": {
              "name": "Infosys Springboard"
            },
            "contact": {
              "email": "support@infy.com"
            }
          },
          "customer": {
            "person": {
              "name": "Jane Doe",
              "age": "13",
              "gender": "female",
              "tags": [
                {
                  "descriptor": {
                    "code": "professional-details",
                    "name": "Professional Details"
                  },
                  "list": [
                    {
                      "descriptor": {
                        "code": "profession",
                        "name": "profession"
                      },
                      "value": "student"
                    }
                  ],
                  "display": true
                }
              ]
            },
            "contact": {
              "phone": "+91-9663088848",
              "email": "jane.doe@example.com"
            }
          }
        }
      ],
      "quote": {
        "price": {
          "currency": "INR",
          "value": "150"
        }
      },
      "billing": {
        "name": "Jane Doe",
        "phone": "+91-9663088848",
        "email": "jane.doe@example.com",
        "address": "No 27, XYZ Lane, etc"
      },
      "payments": [
        {
          "params": {
            "amount": "150",
            "currency": "INR"
          },
          "url": "https://examplepayments.com/pay",
          "type": "PRE-ORDER",
          "status": "PAID",
          "collected_by": "bpp"
        }
      ]
    }
  }
}
  
```

&#x20;         2\. If payment is failed, payment.status is NOT-PAID and payment URL will be shared.

```json
{
  "context": {
    "domain": "onest:learning-experiences",
    "version": "1.1.0",
    "action": "on_init",
    "bap_uri": "https://sample.bap.io/",
    "bap_id": "sample.bap.io",
    "bpp_id": "sample.bpp.io",
    "bpp_uri": "https://sample.bpp.io",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62196",
    "message_id": "d514a38f-e112-4bb8-a3d8-b8e5d8dea82d",
    "ttl": "PT10M",
    "timestamp": "2023-02-20T15:21:36.925Z"
  },
  "message": {
    "order": {
      "provider": {
        "id": "INFOSYS",
        "descriptor": {
          "name": "Infosys Springboard",
          "short_desc": "Infosys Springboard Digital literacy program",
          "images": [
            {
              "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/app_logos/landing-new.png",
              "size_type": "sm"
            }
          ]
        },
        "categories": [
          {
            "id": "LANGUAGE-COURSES",
            "descriptor": {
              "code": "LANGUAGE-COURSES",
              "name": "Language Courses"
            }
          },
          {
            "id": "SKILL-DEVELOPMENT-COURSES",
            "descriptor": {
              "code": "SKILL-DEVELOPMENT-COURSES",
              "name": "Skill development Courses"
            }
          },
          {
            "id": "TECHNICAL-COURSES",
            "descriptor": {
              "code": "TECHNICAL-COURSES",
              "name": "Technical Courses"
            }
          },
          {
            "id": "SELF-PACED-COURSES",
            "descriptor": {
              "code": "SELF-PACED-COURSES",
              "name": "Self Paced Courses"
            }
          }
        ]
      },
      "items": [
        {
          "id": "d4975df5-b18c-4772-80ad-368669856d52",
          "quantity": {
            "maximum": {
                    "count": 1
                   }
          },
          "descriptor": {
            "name": "Everyday Conversational English",
            "short_desc": "Elevate your daily conversations with confidence through our 'Everyday Conversational English' course.",
            "long_desc": "<p><strong>Course Overview:</strong><br>Welcome to 'Everyday Conversational English,' your key to mastering essential language skills for real-life communication. Tailored for all levels, this course offers:</p><ol><li><strong>Practical Vocabulary:</strong><br>Learn everyday expressions for seamless communication.</li><li><strong>Interactive Role-Playing:</strong><br>Apply knowledge through immersive exercises for real-world scenarios.</li><li><strong>Cultural Insights:</strong><br>Gain cultural nuances to connect authentically in conversations.</li><li><strong>Real-Life Scenarios:</strong><br>Navigate common situations with confidence-building tools.</li><li><strong>Quiz Assessments:</strong><br>Reinforce learning through quizzes for ongoing skill development.</li></ol><p><strong>Why Take This Course:</strong></p><ul><li><strong>Personal & Professional Growth:</strong><br>Enhance personal connections and gain a professional edge.</li><li><strong>Cultural Fluency:</strong><br>Understand and engage with diverse cultures confidently.</li><li><strong>Life-Long Skill:</strong><br>Develop a valuable skill applicable across various life stages.</li></ul><p>Join 'Everyday Conversational English' and elevate your communication for meaningful connections and success.</p>",
            "images": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/everyday-conversational-english.png"
              }
            ],
            "media": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english/preview/"
              }
            ]
          },
          "creator": {
            "descriptor": {
              "name": "Prof. Emma Sullivan",
              "short_desc": "Experienced language educator dedicated to fostering practical conversational skills and cultural fluency",
              "long_desc": "Hello, I'm Prof. Emma Sullivan, your guide in 'Everyday Conversational English.' With over a decade of experience, I'm here to make language learning dynamic and culturally enriching. Let's explore practical communication skills together for personal and professional growth. Join me on this exciting journey!",
              "images": [
                {
                  "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/ins/1.png"
                }
              ]
            }
          },
          "price": {
            "currency": "INR",
            "value": "150"
          },
          "category_ids": [
            "LANGUAGE-COURSES",
            "SELF-PACED-COURSES"
          ],
          "rating": "4.5",
          "rateable": true,
          "tags": [
            {
              "descriptor": {
                "code": "content-metadata",
                "name": "Content metadata"
              },
              "list": [
                {
                  "descriptor": {
                    "code": "learner-level",
                    "name": "Learner level"
                  },
                  "value": "Beginner"
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
                    "code": "prerequisite",
                    "name": "Prerequisite"
                  },
                  "value": "Should have a basic understanding of English"
                },
                {
                  "descriptor": {
                    "code": "prerequisite",
                    "name": "Prerequisite"
                  },
                  "value": "Access to a computer or internet to access the course online"
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
              ],
              "display": true
            }
          ]
        }
      ],
      "fulfillments": [
        {
          "agent": {
            "person": {
              "name": "Infosys Springboard"
            },
            "contact": {
              "email": "support@infy.com"
            }
          },
          "customer": {
            "person": {
              "name": "Jane Doe",
              "age": "13",
              "gender": "female",
              "tags": [
                {
                  "descriptor": {
                    "code": "professional-details",
                    "name": "Professional Details"
                  },
                  "list": [
                    {
                      "descriptor": {
                        "code": "profession",
                        "name": "profession"
                      },
                      "value": "student"
                    }
                  ],
                  "display": true
                }
              ]
            },
            "contact": {
              "phone": "+91-9663088848",
              "email": "jane.doe@example.com"
            }
          }
        }
      ],
      "quote": {
        "price": {
          "currency": "INR",
          "value": "150"
        }
      },
      "billing": {
        "name": "Jane Doe",
        "phone": "+91-9663088848",
        "email": "jane.doe@example.com",
        "address": "No 27, XYZ Lane, etc"
      },
      "payments": [
        {
          "params": {
            "amount": "150",
            "currency": "INR"
          },
          "url": "https://examplepayments.com/pay-previous-url",
          "type": "PRE-ORDER",
          "status": "NOT-PAID",
          "collected_by": "bpp"
        },
        {
          "params": {
            "amount": "150",
            "currency": "INR"
          },
          "url": "https://examplepayments.com/pay-new-url",
          "type": "PRE-ORDER",
          "status": "NOT-PAID",
          "collected_by": "bpp"
        }
      ]
    }
  }
}
```

8. BAP sends confirms request to confirm the course subscription.\
   \
   Distributor details(tag) and fields in it are optional. These details are collected by seeker and sent to provider.

#### Confirm API

```json
{
  "context": {
    "domain": "onest:learning-experiences",
    "action": "confirm",
    "version": "1.1.0",
    "bap_uri": "https://sample.bap.io/",
    "bap_id": "sample.bap.io",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62196",
    "message_id": "$bb579fb8-cb82-4824-be12-fcbc405b6608",
    "timestamp": "2022-12-12T09:55:41.161Z",
    "ttl": "PT10M",
    "bpp_id": "sample.bpp.io",
    "bpp_uri": "https://sample.bpp.io"
  },
  "message": {
    "order": {
      "provider": {
        "id": "INFOSYS"
      },
      "items": [
        {
          "id": "d4975df5-b18c-4772-80ad-368669856d52"
        }
      ],
      "billing": {
        "name": "Jane Doe",
        "phone": "+91-9663088848",
        "email": "jane.doe@example.com",
        "address": "No 27, XYZ Lane, etc"
      },
      "fulfillments": [
        {
          "customer": {
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
      "payments": [
        {
          "params": {
            "amount": "150",
            "currency": "INR"
          },
          "status": "PAID"
        }
      ]
    }
  }
}
```

9. BPP sends confirmation of submission of job application.

#### On Confirm API

```json
{
  "context": {
    "domain": "onest:learning-experiences",
    "version": "1.1.0",
    "action": "on_confirm",
    "bap_uri": "https://sample.bap.io/",
    "bap_id": "sample.bap.io",
    "bpp_id": "sample.bpp.io",
    "bpp_uri": "https://sample.bpp.io",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62196",
    "message_id": "d514a38f-e112-4bb8-a3d8-b8e5d8dea82d",
    "ttl": "PT10M",
    "timestamp": "2023-02-20T15:21:36.925Z"
  },
  "message": {
    "order": {
      "id": "12424kh",
      "provider": {
        "id": "INFOSYS",
        "descriptor": {
          "name": "Infosys Springboard",
          "short_desc": "Infosys Springboard Digital literacy program",
          "images": [
            {
              "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/app_logos/landing-new.png",
              "size_type": "sm"
            }
          ]
        },
        "categories": [
          {
            "id": "LANGUAGE-COURSES",
            "descriptor": {
              "code": "LANGUAGE-COURSES",
              "name": "Language Courses"
            }
          },
          {
            "id": "SKILL-DEVELOPMENT-COURSES",
            "descriptor": {
              "code": "SKILL-DEVELOPMENT-COURSES",
              "name": "Skill development Courses"
            }
          },
          {
            "id": "TECHNICAL-COURSES",
            "descriptor": {
              "code": "TECHNICAL-COURSES",
              "name": "Technical Courses"
            }
          },
          {
            "id": "SELF-PACED-COURSES",
            "descriptor": {
              "code": "SELF-PACED-COURSES",
              "name": "Self Paced Courses"
            }
          }
        ]
      },
      "items": [
        {
          "id": "d4975df5-b18c-4772-80ad-368669856d52",
          "quantity": {
            "maximum": {
                    "count": 1
                   }
          },
          "descriptor": {
            "name": "Everyday Conversational English",
            "short_desc": "Elevate your daily conversations with confidence through our 'Everyday Conversational English' course.",
            "long_desc": "<p><strong>Course Overview:</strong><br>Welcome to 'Everyday Conversational English,' your key to mastering essential language skills for real-life communication. Tailored for all levels, this course offers:</p><ol><li><strong>Practical Vocabulary:</strong><br>Learn everyday expressions for seamless communication.</li><li><strong>Interactive Role-Playing:</strong><br>Apply knowledge through immersive exercises for real-world scenarios.</li><li><strong>Cultural Insights:</strong><br>Gain cultural nuances to connect authentically in conversations.</li><li><strong>Real-Life Scenarios:</strong><br>Navigate common situations with confidence-building tools.</li><li><strong>Quiz Assessments:</strong><br>Reinforce learning through quizzes for ongoing skill development.</li></ol><p><strong>Why Take This Course:</strong></p><ul><li><strong>Personal & Professional Growth:</strong><br>Enhance personal connections and gain a professional edge.</li><li><strong>Cultural Fluency:</strong><br>Understand and engage with diverse cultures confidently.</li><li><strong>Life-Long Skill:</strong><br>Develop a valuable skill applicable across various life stages.</li></ul><p>Join 'Everyday Conversational English' and elevate your communication for meaningful connections and success.</p>",
            "images": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/everyday-conversational-english.png"
              }
            ],
            "media": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english/preview/"
              }
            ]
          },
          "creator": {
            "descriptor": {
              "name": "Prof. Emma Sullivan",
              "short_desc": "Experienced language educator dedicated to fostering practical conversational skills and cultural fluency",
              "long_desc": "Hello, I'm Prof. Emma Sullivan, your guide in 'Everyday Conversational English.' With over a decade of experience, I'm here to make language learning dynamic and culturally enriching. Let's explore practical communication skills together for personal and professional growth. Join me on this exciting journey!",
              "images": [
                {
                  "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/ins/1.png"
                }
              ]
            }
          },
          "price": {
            "currency": "INR",
            "value": "150"
          },
          "category_ids": [
            "LANGUAGE-COURSES",
            "SELF-PACED-COURSES"
          ],
          "rating": "4.5",
          "rateable": true,
          "add-ons": [
            {
              "id": "course-outline",
              "descriptor": {
                "name": "Course Outline",
                "long_desc": "Outline for the course",
                "media": [
                  {
                    "mimetype": "application/pdf",
                    "url": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english/outline.pdf"
                  }
                ]
              }
            },
            {
              "id": "prelim-quiz",
              "descriptor": {
                "name": "Preliminary Quiz",
                "long_desc": "Take this preliminary quiz to see if you will benefit from the course!",
                "media": [
                  {
                    "mimetype": "text/html",
                    "url": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english/prelim-quiz"
                  }
                ]
              }
            }
          ],
          "tags": [
            {
              "descriptor": {
                "code": "content-metadata",
                "name": "Content metadata"
              },
              "list": [
                {
                  "descriptor": {
                    "code": "learner-level",
                    "name": "Learner level"
                  },
                  "value": "Beginner"
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
                    "code": "prerequisite",
                    "name": "Prerequisite"
                  },
                  "value": "Should have a basic understanding of English"
                },
                {
                  "descriptor": {
                    "code": "prerequisite",
                    "name": "Prerequisite"
                  },
                  "value": "Access to a computer or internet to access the course online"
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
              ],
              "display": true
            }
          ]
        }
      ],
      "fulfillments": [
        {
          "state": {
            "descriptor": {
              "code": "NOT-STARTED",
              "name": "Not Started"
            },
            "updated_at": "2023-02-06T09:55:41.161Z"
          },
          "agent": {
            "person": {
              "name": "Infosys Springboard"
            },
            "contact": {
              "email": "support@infy.com"
            }
          },
          "customer": {
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
          "stops": [
            {
              "id": "0",
              "instructions": {
                "name": "content-video-1",
                "long_desc": "Description About the Content",
                "media": [
                  {
                    "mimetype": "video/mp4",
                    "url": "https://embedded-video-player-url/play"
                  }
                ]
              }
            },
            {
              "id": "1",
              "instructions": {
                "name": "content-video-2",
                "long_desc": "Description About the Content",
                "media": [
                  {
                    "mimetype": "video/mp4",
                    "url": "https://embedded-video-player-url/play"
                  }
                ]
              }
            },
            {
              "id": "2",
              "instructions": {
                "name": "content-pdf",
                "long_desc": "Description About the Content",
                "media": [
                  {
                    "mimetype": "application/pdf",
                    "url": "https://link-to-the-document/"
                  }
                ]
              }
            }
          ],
          "tags": [
            {
              "descriptor": {
                "code": "course-completion-details",
                "name": "Content Completion Details"
              },
              "list": [
                {
                  "descriptor": {
                    "code": "course-certificate",
                    "name": "Course certificate"
                  },
                  "value": "https://link-to-certificate"
                },
                {
                  "descriptor": {
                    "code": "course-badge",
                    "name": "Course Badge"
                  },
                  "value": "https://link-to-badge"
                }
              ],
              "display": true
            }
          ]
        }
      ],
      "quote": {
        "price": {
          "currency": "INR",
          "value": "150"
        }
      },
      "billing": {
        "name": "Jane Doe",
        "phone": "+91-9663088848",
        "email": "jane.doe@example.com",
        "address": "No 27, XYZ Lane, etc"
      },
      "payments": [
        {
          "params": {
            "amount": "150",
            "currency": "INR"
          },
          "type": "PRE-ORDER",
          "status": "PAID",
          "collected_by": "bpp"
        }
      ]
    }
  }
}

```

10. BAP receives the on\_confirm, which contains the embeddable URLs to the contents. The contents can be videos, pdf etc.
11. BAP can use the status API to fetch the course status.

#### Status API

```json
{
  "context": {
    "domain": "onest:learning-experiences",
    "action": "status",
    "version": "1.1.0",
    "bap_uri": "https://sample.bap.io/",
    "bap_id": "sample.bap.io",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62196",
    "message_id": "$bb579fb8-cb82-4824-be12-fcbc405b6608",
    "timestamp": "2022-12-12T09:55:41.161Z",
    "ttl": "PT10M",
    "bpp_id": "sample.bpp.io",
    "bpp_uri": "https://sample.bpp.io"
  },
  "message": {
    "order": {
      "id": "12424kh"
    }
  }
}
```

12. BPP send the on\_status request, with course status and certification details (if course is completed).

#### On Status API

```json
{
  "context": {
    "domain": "onest:learning-experiences",
    "version": "1.1.0",
    "action": "on_status",
    "bap_uri": "https://sample.bap.io/",
    "bap_id": "sample.bap.io",
    "bpp_id": "sample.bpp.io",
    "bpp_uri": "https://sample.bpp.io",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62196",
    "message_id": "d514a38f-e112-4bb8-a3d8-b8e5d8dea82d",
    "ttl": "PT10M",
    "timestamp": "2023-02-20T15:21:36.925Z"
  },
  "message": {
    "order": {
      "id": "12424kh",
      "provider": {
        "id": "INFOSYS",
        "descriptor": {
          "name": "Infosys Springboard",
          "short_desc": "Infosys Springboard Digital literacy program",
          "images": [
            {
              "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/app_logos/landing-new.png",
              "size_type": "sm"
            }
          ]
        },
        "categories": [
          {
            "id": "LANGUAGE-COURSES",
            "descriptor": {
              "code": "LANGUAGE-COURSES",
              "name": "Language Courses"
            }
          },
          {
            "id": "SKILL-DEVELOPMENT-COURSES",
            "descriptor": {
              "code": "SKILL-DEVELOPMENT-COURSES",
              "name": "Skill development Courses"
            }
          },
          {
            "id": "TECHNICAL-COURSES",
            "descriptor": {
              "code": "TECHNICAL-COURSES",
              "name": "Technical Courses"
            }
          },
          {
            "id": "SELF-PACED-COURSES",
            "descriptor": {
              "code": "SELF-PACED-COURSES",
              "name": "Self Paced Courses"
            }
          }
        ]
      },
      "items": [
        {
          "id": "d4975df5-b18c-4772-80ad-368669856d52",
          "quantity": {
            "maximum": {
                    "count": 1
                   }
          },
          "descriptor": {
            "name": "Everyday Conversational English",
            "short_desc": "Elevate your daily conversations with confidence through our 'Everyday Conversational English' course.",
            "long_desc": "<p><strong>Course Overview:</strong><br>Welcome to 'Everyday Conversational English,' your key to mastering essential language skills for real-life communication. Tailored for all levels, this course offers:</p><ol><li><strong>Practical Vocabulary:</strong><br>Learn everyday expressions for seamless communication.</li><li><strong>Interactive Role-Playing:</strong><br>Apply knowledge through immersive exercises for real-world scenarios.</li><li><strong>Cultural Insights:</strong><br>Gain cultural nuances to connect authentically in conversations.</li><li><strong>Real-Life Scenarios:</strong><br>Navigate common situations with confidence-building tools.</li><li><strong>Quiz Assessments:</strong><br>Reinforce learning through quizzes for ongoing skill development.</li></ol><p><strong>Why Take This Course:</strong></p><ul><li><strong>Personal & Professional Growth:</strong><br>Enhance personal connections and gain a professional edge.</li><li><strong>Cultural Fluency:</strong><br>Understand and engage with diverse cultures confidently.</li><li><strong>Life-Long Skill:</strong><br>Develop a valuable skill applicable across various life stages.</li></ul><p>Join 'Everyday Conversational English' and elevate your communication for meaningful connections and success.</p>",
            "images": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/everyday-conversational-english.png"
              }
            ],
            "media": [
              {
                "url": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english/preview/"
              }
            ]
          },
          "creator": {
            "descriptor": {
              "name": "Prof. Emma Sullivan",
              "short_desc": "Experienced language educator dedicated to fostering practical conversational skills and cultural fluency",
              "long_desc": "Hello, I'm Prof. Emma Sullivan, your guide in 'Everyday Conversational English.' With over a decade of experience, I'm here to make language learning dynamic and culturally enriching. Let's explore practical communication skills together for personal and professional growth. Join me on this exciting journey!",
              "images": [
                {
                  "url": "https://infyspringboard.onwingspan.com/web/assets/images/infosysheadstart/ins/1.png"
                }
              ]
            }
          },
          "price": {
            "currency": "INR",
            "value": "150"
          },
          "category_ids": [
            "LANGUAGE-COURSES",
            "SELF-PACED-COURSES"
          ],
          "rating": "4.5",
          "rateable": true,
          "add-ons": [
            {
              "id": "course-outline",
              "descriptor": {
                "name": "Course Outline",
                "long_desc": "Outline for the course",
                "media": [
                  {
                    "mimetype": "application/pdf",
                    "url": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english/outline.pdf"
                  }
                ]
              }
            },
            {
              "id": "prelim-quiz",
              "descriptor": {
                "name": "Preliminary Quiz",
                "long_desc": "Take this preliminary quiz to see if you will benefit from the course!",
                "media": [
                  {
                    "mimetype": "text/html",
                    "url": "https://infyspringboard.onwingspan.com/web/courses/infosysheadstart/everyday-conversational-english/prelim-quiz"
                  }
                ]
              }
            }
          ],
          "tags": [
            {
              "descriptor": {
                "code": "content-metadata",
                "name": "Content metadata"
              },
              "list": [
                {
                  "descriptor": {
                    "code": "learner-level",
                    "name": "Learner level"
                  },
                  "value": "Beginner"
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
                    "code": "prerequisite",
                    "name": "Prerequisite"
                  },
                  "value": "Should have a basic understanding of English"
                },
                {
                  "descriptor": {
                    "code": "prerequisite",
                    "name": "Prerequisite"
                  },
                  "value": "Access to a computer or internet to access the course online"
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
              ],
              "display": true
            }
          ]
        }
      ],
      "fulfillments": [
        {
          "state": {
            "descriptor": {
              "code": "COMPLETED",
              "name": "Completed"
            },
            "updated_at": "2023-02-06T09:55:41.161Z"
          },
          "agent": {
            "person": {
              "name": "Infosys Springboard"
            },
            "contact": {
              "email": "support@infy.com"
            }
          },
          "customer": {
            "person": {
              "name": "Jane Doe",
              "age": "13",
              "gender": "female",
              "tags": [
                {
                  "descriptor": {
                    "code": "professional-details",
                    "name": "Professional Details"
                  },
                  "list": [
                    {
                      "descriptor": {
                        "code": "profession",
                        "name": "profession"
                      },
                      "value": "student"
                    }
                  ],
                  "display": true
                }
              ]
            },
            "contact": {
              "phone": "+91-9663088848",
              "email": "jane.doe@example.com"
            }
          },
          "stops": [
            {
              "id": "0",
              "instructions": {
                "name": "content-video-1",
                "long_desc": "Description About the Content",
                "media": [
                  {
                    "mimetype": "video/mp4",
                    "url": "https://embedded-video-player-url/play"
                  }
                ]
              }
            },
            {
              "id": "1",
              "instructions": {
                "name": "content-video-2",
                "long_desc": "Description About the Content",
                "media": [
                  {
                    "mimetype": "video/mp4",
                    "url": "https://embedded-video-player-url/play"
                  }
                ]
              }
            },
            {
              "id": "2",
              "instructions": {
                "name": "content-pdf",
                "long_desc": "Description About the Content",
                "media": [
                  {
                    "mimetype": "application/pdf",
                    "url": "https://link-to-the-document/"
                  }
                ]
              }
            }
          ],
          "tags": [
            {
              "descriptor": {
                "code": "course-completion-details",
                "name": "Content Completion Details"
              },
              "list": [
                {
                  "descriptor": {
                    "code": "course-certificate",
                    "name": "Course certificate"
                  },
                  "value": "https://link-to-certificate"
                },
                {
                  "descriptor": {
                    "code": "course-badge",
                    "name": "Course Badge"
                  },
                  "value": "https://link-to-badge"
                }
              ],
              "display": true
            }
          ]
        }
      ],
      "quote": {
        "price": {
          "currency": "INR",
          "value": "150"
        }
      },
      "billing": {
        "name": "Jane Doe",
        "phone": "+91-9663088848",
        "email": "jane.doe@example.com",
        "address": "No 27, XYZ Lane, etc"
      },
      "payments": [
        {
          "params": {
            "amount": "150",
            "currency": "INR"
          },
          "type": "PRE-ORDER",
          "status": "PAID",
          "collected_by": "bpp"
        }
      ]
    }
  }
}
```

### Enums

1. Fulfillment.status values

| code        | name        |
| ----------- | ----------- |
| NOT-STARTED | Not Started |
| IN-PROGRESS | In Progress |
| COMPLETED   | Completed   |
| ACTIVE      | Active      |
| EXPIRED     | Expired     |


# Course with scholarship

Imagine a use-case where a course provider is also offering scholarship as an option for the user. Below is a reference implementation guide for the same.

<figure><img src="https://static.swimlanes.io/ac7a24591ccaa4cb39a1bd8a377c7ccd.png" alt=""><figcaption><p>Course with scholarship</p></figcaption></figure>

To edit the above diagram, visit: [https://swimlanes.io/u/34SSWwoC8](https://swimlanes.io/u/34SSWwoC8). For feedback or suggestion, initiate a discussion at [https://github.com/orgs/ONEST-Network/discussions](https://github.com/orgs/ONEST-Network/discussions)

### API Flow

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

#### On Search API

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

4. BPP will receive the select request and check if the course is still valid. If the course is still valid, the BPP will send the on\_select call with complete details of the course and scholarships (if applicable to the course) as offers.

#### On Select API

Order object contains the offers which includes the scholarship details and BPP details. If users wants to apply to the scholarship, BAP can start the financial support API flow from  [#init-api](../financial-support/#init-api "mention")&#x20;

Financial Support APIs:

init API - It is used to initiate the scholarship application.

on\_init API - It contains the scholarship details and xinput form to collect the user details.

confirm API - To confirm the scholarship application.

on\_confirm API - It contains scholarship confirmation details.

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
      "offers": [
        {
          "id": "scholarship-1",
          "descriptor": {
            "name": "XYZ Education Scholarship",
            "short_desc": "XYZ Education Scholarship for Undergraduate Students",
            "images": [
              {
                "url": "http://url-to-image"
              }
            ]
          },
          "item_ids": [
            "d4975df5-b18c-4772-80ad-368669856d52"
          ],
          "tags": [
            {
              "descriptor": {
                "code": "scholarship-metadata",
                "name": "Scholarship Metadata"
              },
              "list": [
                {
                  "descriptor": {
                    "code": "scholarship-bpp-id"
                  },
                  "value": "sample.bpp.io"
                },
                {
                  "descriptor": {
                    "code": "scholarship-bpp-uri"
                  },
                  "value": "https://sample.bpp.io"
                },
                {
                  "descriptor": {
                    "code": "scholarship-provider-id"
                  },
                  "value": "provider-1"
                },
                {
                  "descriptor": {
                    "code": "scholarship-item-id"
                  },
                  "value": "scholarship-1"
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

5. Use the order id from financial support flow on\_confirm API in the init, to initiate the course.

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
      "offer": [
        {
          "id": "scholarship-1",
          "tags": [
            {
              "descriptor": {
                "code": "scholarship-application-metadata",
                "name": "Scholarship Application Metadata"
              },
              "list": [
                {
                  "descriptor": {
                    "code": "scholarship-id"
                  },
                  "value": "12424kh"
                }
              ],
              "display": true
            }
          ]
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

6. Confirmation for the course initiation.

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
          "type": "PRE-ORDER",
          "status": "PAID",
          "collected_by": "bpp"
        }
      ]
    }
  }
}
```

7. BAP sends confirms request to confirm the course subscription.

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
          }
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

8. BPP sends confirmation of submission of job application.

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

9. BAP receives the on\_confirm, which contains the embeddable URLs to the contents. The contents can be videos, pdf etc.
10. BAP can use the status API to fetch the course status.

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

11. BPP send the on\_status request, with course status and certification details (if course is completed).

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

# Work Opportunities

### Use-case:

Job Hub is acting as provider platform(BPP) which hosts the jobs and Worker Hub is acting as seeker platform(BAP) which helps the workers to find jobs.

### Flow Diagram:

<figure><img src="../../assets/work-opportunities-flow.png" alt=""><figcaption></figcaption></figure>

### API Mapping and Sample JSON's:

1. BAP will make search request with an intent, ex: job name, job provider, location etc.

<details>

<summary>Search API - Search By job name</summary>

```json
{
    "context": {
        "domain": "onest:work-opportunities",
        "action": "search",
        "version": "1.1.0",
        "bap_id": "worker-hub.bap.io",
        "bap_uri": "https://worker-hub.bap.io/",
        "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
        "message_id": "$89bdae17-9942-40c8-869a-5bd413356407",
        "timestamp": "2022-10-11T09:55:41.161Z",
        "ttl": "PT30S"
    },
    "message": {
        "intent": {
            "item": {
                "descriptor": {
                    "name": "Engineer"
                }
            }
        }
    }
}
```

</details>

<details>

<summary>Search API - Search By job provider</summary>

```json
{
    "context": {
        "domain": "onest:work-opportunities",
        "action": "search",
        "version": "1.1.0",
        "bap_id": "worker-hub.bap.io",
        "bap_uri": "https://worker-hub.bap.io/",
        "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
        "message_id": "$89bdae17-9942-40c8-869a-5bd413356407",
        "timestamp": "2022-10-11T09:55:41.161Z",
        "ttl": "PT30S"
    },
    "message": {
        "intent": {
            "provider": {
                "descriptor": {
                    "name": "ABC Tech"
                }
            }
        }
    }
}
```

</details>

<details>

<summary>Search API - Search By location of the Job</summary>

<pre class="language-json"><code class="lang-json">{
    "context": {
        "domain": "onest:work-opportunities",
        "action": "search",
        "version": "1.1.0",
        "bap_id": "worker-hub.bap.io",
        "bap_uri": "https://worker-hub.bap.io/",
        "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
        "message_id": "$89bdae17-9942-40c8-869a-5bd413356407",
        "timestamp": "2022-10-11T09:55:41.161Z",
        "ttl": "PT30S"
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
<strong>}
</strong></code></pre>

The seeker apps can provide geographical locations where it requires job listings based out of. Here country object is optional as state ISO code already denotes the country code as well. Please note caching by country alone may result in the influx of high number of listings.&#x20;

</details>

<details>

<summary>Search API - Search by user details</summary>

Seeker can search using the age, gender and skills of the user.

```json
{
  "context": {
    "domain": "onest:work-opportunities",
    "action": "search",
    "version": "1.1.0",
    "bap_id": "worker-hub.bap.io",
    "bap_uri": "https://worker-hub.bap.io/",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
    "message_id": "$89bdae17-9942-40c8-869a-5bd413356407",
    "timestamp": "2022-10-11T09:55:41.161Z",
    "ttl": "PT30S"
  },
  "message": {
    "intent": {
      "fulfillment": {
        "customer": {
          "person": {
            "age": "25",
            "gender": "male",
            "skills": [
              {
                "code": "ASSEMBLY-OPERATOR",
                "name": "Assembly Operator"
              },
              {
                "code": "ELECTRICIAN",
                "name": "Electrician"
              }
            ]
          }
        }
      }
    }
  }
}
```

</details>

<details>

<summary>Search API - Search by industry type</summary>

```json
{
	"context": {
		"domain": "onest:work-opportunities",
		"action": "search",
		"version": "1.1.0",
		"bap_id": "worker-hub.bap.io",
		"bap_uri": "https://worker-hub.bap.io/",
		"transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
		"message_id": "$89bdae17-9942-40c8-869a-5bd413356407",
		"timestamp": "2022-10-11T09:55:41.161Z",
		"ttl": "PT30S"
	},
	"message": {
		"intent": {
			"item": {
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

<summary>Search API - Search by employment type</summary>

```json
{
	"context": {
		"domain": "onest:work-opportunities",
		"action": "search",
		"version": "1.1.0",
		"bap_id": "worker-hub.bap.io",
		"bap_uri": "https://worker-hub.bap.io/",
		"transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
		"message_id": "$89bdae17-9942-40c8-869a-5bd413356407",
		"timestamp": "2022-10-11T09:55:41.161Z",
		"ttl": "PT30S"
	},
	"message": {
		"intent": {
			"item": {
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
									"code": "employment-type",
									"name": "Employment type"
								},
								"value": "full-time",
								"display": true
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

Searches may be used by the seeker apps to cache responses basis the intent as well.&#x20;

2. BPP will create a catalogue containing jobs with matching criteria and sends it as on\_search request.

<details>

<summary>On Search API</summary>

The request will contain only minimal details about the job like job name, job description, location etc.

```json
{
	"context": {
		"domain": "onest:work-opportunities",
		"action": "on_search",
		"version": "1.1.0",
		"bap_id": "worker-hub.bap.io",
		"bap_uri": "https://worker-hub.bap.io",
		"bpp_id": "job-hub.bpp.io",
		"bpp_uri": "https://job-hub.bpp.io",
		"transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
		"message_id": "672f774c-4281-44dd-b1c2-84222a3d771e",
		"timestamp": "2023-02-22T11:45:10.1712958+00:00",
		"ttl": "P1M"
	},
	"message": {
		"catalog": {
			"descriptor": {
				"name": "Affindi Jobs"
			},
			"providers": [
				{
					"id": "1",
					"descriptor": {
						"name": "Affinidi",
						"short_desc": "Short Description about the company",
						"images": [
							{
								"url": "url of the image of the provider"
							}
						]
					},
					"fulfillments": [
						{
							"id": "1",
							"type": "REMOTE"
						},
						{
							"id": "2",
							"type": "HYBRID"
						},
						{
							"id": "3",
							"type": "ONSITE"
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
						},
						{
							"id": "L3",
							"city": {
								"name": "Lucknow",
								"code": "std:0522"
							},
							"state": {
								"name": "Uttar Pradesh",
								"code": "UP"
							}
						}
					],
					"items": [
						{
							"id": "D7F8606A370DA9966DF15E62A81C374B",
							"descriptor": {
								"name": "Database Engineer",
								"long_desc": "We’re on a search for a Staff Mobile Developer with the following attributes: Critical Thinking- You are able to skillfully conceptualise, apply, analyse and evaluate information gathered from observation, experience or communication and use it as a guide to action Data-Driven attitude — You often propose solutions or make a point in a logical and objective manner, substantiated with accurate data and evidence Dealing with Ambiguity — You can effectively cope with change and uncertainty, and are comfortable when things are up in the air Goal-oriented — You are driven and can be counted on to exceed goals. You steadfastly push yourself and others to achieve results all the time Problem Solving — You can easily identify and solve complex problems in a methodological manner ",
								"media": [
									{
										"mimetype": "audio/mp4",
										"url": "http://url-to-audio-about-job"
									},
									{
										"mimetype": "video/mp4",
										"url": "http://url-to-video-about-job"
									}
								]
							},
							"quantity": {
								"available": {
									"count": 150
								}
							},
							"location_ids": [
								"L1"
							],
							"fulfillment_ids": [
								"1",
								"2",
								"3"
							],
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
								},
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
								},
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
								},
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
								},
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
						},
						{
							"id": "0253719F295521CED39EC9C2F3C8DCDE",
							"descriptor": {
								"name": "Fullstack Engineer",
								"long_desc": "We’re on a search for a Staff Mobile Developer with the following attributes: Critical Thinking- You are able to skillfully conceptualise, apply, analyse and evaluate information gathered from observation, experience or communication and use it as a guide to action Data-Driven attitude — You often propose solutions or make a point in a logical and objective manner, substantiated with accurate data and evidence Dealing with Ambiguity — You can effectively cope with change and uncertainty, and are comfortable when things are up in the air Goal-oriented — You are driven and can be counted on to exceed goals. You steadfastly push yourself and others to achieve results all the time Problem Solving — You can easily identify and solve complex problems in a methodological manner",
								"media": [
									{
										"mimetype": "audio/mp4",
										"url": "http://url-to-audio-about-job"
									},
									{
										"mimetype": "video/mp4",
										"url": "http://url-to-video-about-job"
									}
								]
							},
							"quantity": {
								"available": {
									"count": 50
								}
							},
							"location_ids": [
								"L2"
							],
							"fulfillment_ids": [
								"1",
								"2",
								"3"
							],
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
								},
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
								},
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
								},
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
								},
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
			]
		}
	}
}
```

</details>

3. BAP will receive the on\_search request and displays the list of jobs to the user. Once the user chooses a job, BAP will make select API with item ID to get the complete details about the job.

<details>

<summary>Select API</summary>

```json
{
    "context": {
        "domain": "onest:work-opportunities",
        "action": "select",
        "version": "1.1.0",
        "bap_id": "worker-hub.bap.io",
        "bap_uri": "https://worker-hub.bap.io",
        "bpp_id": "job-hub.bpp.io",
        "bpp_uri": "https://job-hub.bpp.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
        "message_id": "$89bdae17-9942-40c8-869a-5bd413356407",
        "timestamp": "2023-02-14T12:11:46.1295616+00:00",
        "ttl": "P1M"
    },
    "message": {
        "order": {
            "provider": {
                "id": "1"
            },
            "items": [
                {
                    "id": "a23f2fdfbbb8ac402bf259d75402eb0792f50c095f7d08a55475e7af1c2dadca"
                }
            ]
        }
    }
}
```

</details>

4. BPP will receive the select request and check if the listing is still valid. If the listing is still valid, BPP will send the on\_select call with complete details of the job listing

<details>

<summary>On Select API</summary>

```json
{
    "context": {
        "domain": "onest:work-opportunities",
        "version": "1.1.0",
        "action": "on_select",
        "bap_id": "worker-hub.bap.io",
        "bap_uri": "https://worker-hub.bap.io",
        "bpp_id": "job-hub.bpp.io",
        "bpp_uri": "https://job-hub.bpp.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
        "message_id": "c8e3968c-cd78-4e46-aa34-0d541e46bd73",
        "ttl": "PT10M",
        "timestamp": "2023-02-22T11:50:46.742Z"
    },
    "message": {
        "order": {
            "provider": {
                "id": "1",
                "descriptor": {
                    "name": "Affinidi"
                },
                "fulfillments": [
                    {
                        "id": "1",
                        "type": "REMOTE"
                    },
                    {
                        "id": "2",
                        "type": "HYBRID"
                    },
                    {
                        "id": "3",
                        "type": "ONSITE"
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
                    }
                ]
            },
            "items": [
                {
                    "id": "0253719F295521CED39EC9C2F3C8DCDE",
                    "descriptor": {
                        "name": "Fullstack Engineer",
                        "long_desc": "We’re on a search for a Staff Mobile Developer with the following attributes: Critical Thinking- You are able to skillfully conceptualise, apply, analyse and evaluate information gathered from observation, experience or communication and use it as a guide to action Data-Driven attitude — You often propose solutions or make a point in a logical and objective manner, substantiated with accurate data and evidence Dealing with Ambiguity — You can effectively cope with change and uncertainty, and are comfortable when things are up in the air Goal-oriented — You are driven and can be counted on to exceed goals. You steadfastly push yourself and others to achieve results all the time Problem Solving — You can easily identify and solve complex problems in a methodological manner "
                    },
                    "fulfillment_ids": [
                        "1",
                        "2",
                        "3"
                    ],
                    "location_ids": [
                        "L1"
                    ],
                    "time": {
                        "range": {
                            "start": "2023-01-03T13:23:01+00:00",
                            "end": "2023-02-03T13:23:01+00:00"
                        }
                    },
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
                        },
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
                        },
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
                        },
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
                        },
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
```

</details>

5. BAP sends the customer details to the BPP in the init API. This is the initializing step of the job application process.

<details>

<summary>Init API</summary>

```json
{
    "context": {
        "domain": "onest:work-opportunities",
        "action": "init",
        "version": "1.1.0",
        "bap_id": "worker-hub.bap.io",
        "bap_uri": "https://worker-hub.bap.io",
        "bpp_id": "job-hub.bpp.io",
        "bpp_uri": "https://job-hub.bpp.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
        "message_id": "$89bdae17-9942-40c8-869a-5bd413356407",
        "timestamp": "2023-02-14T12:11:46.1295616+00:00",
        "ttl": "P1M"
    },
    "message": {
        "order": {
            "provider": {
                "id": "1"
            },
            "items": [
                {
                    "id": "a23f2fdfbbb8ac402bf259d75402eb0792f50c095f7d08a55475e7af1c2dadca",
                    "fulfillment_ids": [
                        "1"
                    ]
                }
            ],
            "fulfillments": [
                {
                    "id": "1",
                    "customer": {
                        "person": {
                            "name": "Sanjay",
                            "gender": "Male",
                            "age": "35",
                            "skills": [
                                {
                                    "code": "Android",
                                    "name": "Android"
                                },
                                {
                                    "code": "AWS",
                                    "name": "AWS"
                                }
                            ],
                            "languages": [
                                {
                                    "code": "en",
                                    "name": "english"
                                },
                                {
                                    "code": "ml",
                                    "name": "Malayalam"
                                },
                                {
                                    "code": "hi",
                                    "name": "Hindi"
                                }
                            ],
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
                                },
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
                        },
                        "contact": {
                            "phone": "9999999999999",
                            "email": "abc@abc.bc"
                        }
                    }
                }
            ]
        }
    }
}
```

</details>

6. If BPP wants to collect additional details of the user, it will send an xinput form in the on\_init request.\
   \
   If BPP has multiple forms to collect the data, it will make on\_init request with the form number(current index) and total number of forms(max index). BPP should generate the xinput form with transaction id(request.context.transaction\_id) so that the forms can be tagged with an order lifecycle.\
   \
   BAP should render the xinput form on the UI and collect all the details.\
   \
   If there are no required xinput forms, the BAP can confirm the order via /confirm API.\
   \
   [Example](https://github.com/beckn/DSEP-Specification/blob/draft/examples/financial-support/forms/scholarship-application-form.html) of xinput form and [recommendations](https://github.com/beckn/protocol-specifications/blob/master/docs/BECKN-007-The-XInput-Schema.md) to create xinput form.

<details>

<summary>On Init API</summary>

```json
{
    "context": {
        "domain": "onest:work-opportunities",
        "action": "on_init",
        "version": "1.1.0",
        "bap_id": "worker-hub.bap.io",
        "bap_uri": "https://worker-hub.bap.io",
        "bpp_id": "job-hub.bpp.io",
        "bpp_uri": "https://job-hub.bpp.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
        "message_id": "af58aa7b-6745-47d0-9b0d-62dcb262ee87",
        "timestamp": "2023-02-23T10:14:05.5579055+00:00",
        "ttl": "P1M"
    },
    "message": {
        "order": {
            "provider": {
                "id": "1",
                "descriptor": {
                    "name": "Affinidi"
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
                    }
                ]
            },
            "items": [
                {
                    "id": "a23f2fdfbbb8ac402bf259d75402eb0792f50c095f7d08a55475e7af1c2dadca",
                    "descriptor": {
                        "name": "Fullstack Engineer",
                        "long_desc": "We’re on a search for a Staff Mobile Developer with the following attributes: Critical Thinking- You are able to skillfully conceptualise, apply, analyse and evaluate information gathered from observation, experience or communication and use it as a guide to action Data-Driven attitude — You often propose solutions or make a point in a logical and objective manner, substantiated with accurate data and evidence Dealing with Ambiguity — You can effectively cope with change and uncertainty, and are comfortable when things are up in the air Goal-oriented — You are driven and can be counted on to exceed goals. You steadfastly push yourself and others to achieve results all the time Problem Solving — You can easily identify and solve complex problems in a methodological manner "
                    },
                    "fulfillment_ids": [
                        "1"
                    ],
                    "location_ids": [
                        "L1"
                    ],
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
                                "max": 0
                            },
                            "headings": [
                                "Candidate Details"
                            ]
                        },
                        "form": {
                            "mime_type": "text/html",
                            "url": "https://6vs8xnx5i7.jobhub.co.in/loans-kyc/xinput/formid/a23f2fdfbbb8ac402bfd54f-1",
                            "resubmit": false
                        }
                    },
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
                        },
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
                        },
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
                        },
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
                        },
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
            ],
            "fulfillments": [
                {
                    "id": "1",
                    "type": "REMOTE",
                    "state": {
                        "descriptor": {
                            "code": "APPLICATION-STARTED",
                            "name": "Application started"
                        },
                        "updated_at": "2023-02-06T09:55:41.161Z"
                    },
                    "customer": {
                        "person": {
                            "name": "Sanjay",
                            "gender": "Male",
                            "age": "35",
                            "skills": [
                                {
                                    "code": "Android",
                                    "name": "Android"
                                },
                                {
                                    "code": "AWS",
                                    "name": "AWS"
                                }
                            ],
                            "languages": [
                                {
                                    "code": "en",
                                    "name": "english"
                                },
                                {
                                    "code": "ml",
                                    "name": "Malayalam"
                                },
                                {
                                    "code": "hi",
                                    "name": "Hindi"
                                }
                            ],
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
                                },
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
                        },
                        "contact": {
                            "phone": "9999999999999",
                            "email": "abc@abc.bc"
                        }
                    }
                }
            ]
        }
    }
}
```

Here in this example the BPP has only one form to send. So the cur, min and max values in xinput object will be 0. Fulfillment status code will be `APPLICATION-STARTED`.

</details>

<details>

<summary>On Init API - Step 2 (post form submission)</summary>

```json
{
    "context": {
        "domain": "onest:work-opportunities",
        "action": "on_init",
        "version": "1.1.0",
        "bap_id": "worker-hub.bap.io",
        "bap_uri": "https://worker-hub.bap.io",
        "bpp_id": "job-hub.bpp.io",
        "bpp_uri": "https://job-hub.bpp.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
        "message_id": "af58aa7b-6745-47d0-9b0d-62dcb262ee87",
        "timestamp": "2023-02-23T10:14:05.5579055+00:00",
        "ttl": "P1M"
    },
    "message": {
        "order": {
            "provider": {
                "descriptor": {
                    "name": "Affinidi"
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
                    }
                ]
            },
            "items": [
                {
                    "id": "a23f2fdfbbb8ac402bf259d75402eb0792f50c095f7d08a55475e7af1c2dadca",
                    "descriptor": {
                        "name": "Fullstack Engineer",
                        "long_desc": "We’re on a search for a Staff Mobile Developer with the following attributes: Critical Thinking- You are able to skillfully conceptualise, apply, analyse and evaluate information gathered from observation, experience or communication and use it as a guide to action Data-Driven attitude — You often propose solutions or make a point in a logical and objective manner, substantiated with accurate data and evidence Dealing with Ambiguity — You can effectively cope with change and uncertainty, and are comfortable when things are up in the air Goal-oriented — You are driven and can be counted on to exceed goals. You steadfastly push yourself and others to achieve results all the time Problem Solving — You can easily identify and solve complex problems in a methodological manner "
                    },
                    "fulfillment_ids": [
                        "1"
                    ],
                    "location_ids": [
                        "L1"
                    ],
                    "time": {
                        "range": {
                            "start": "2023-01-03T13:23:01+00:00",
                            "end": "2023-02-03T13:23:01+00:00"
                        }
                    },
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
                        },
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
                        },
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
                        },
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
                        },
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
            ],
            "fulfillments": [
                {
                    "id": "1",
                    "type": "REMOTE",
                    "state": {
                        "descriptor": {
                            "code": "APPLICATION-FILLED",
                            "name": "Application Filled"
                        },
                        "updated_at": "2023-02-06T09:55:41.161Z"
                    },
                    "customer": {
                        "person": {
                            "name": "Sanjay",
                            "gender": "Male",
                            "age": "35",
                            "skills": [
                                {
                                    "code": "Android",
                                    "name": "Android"
                                },
                                {
                                    "code": "AWS",
                                    "name": "AWS"
                                }
                            ],
                            "languages": [
                                {
                                    "code": "en",
                                    "name": "english"
                                },
                                {
                                    "code": "ml",
                                    "name": "Malayalam"
                                },
                                {
                                    "code": "hi",
                                    "name": "Hindi"
                                }
                            ],
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
                                },
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
                        },
                        "contact": {
                            "phone": "9999999999999",
                            "email": "abc@abc.bc"
                        }
                    }
                }
            ]
        }
    }
}
```

Once the form has been submitted the BPP will send on\_init without any form. Fulfillment status code will be `APPLICATION-FILLED`.

</details>

7. BAP confirms user wants to submit the job application.\
   \
   Distributor details(tag) and fields in it are optional. These details are collected by seeker and sent to provider.

<details>

<summary>Confirm API</summary>

```json
{
  "context": {
    "domain": "onest:work-opportunities",
    "version": "1.1.0",
    "action": "confirm",
    "bap_id": "worker-hub.bap.io",
    "bap_uri": "https://worker-hub.bap.io",
    "bpp_id": "job-hub.bpp.io",
    "bpp_uri": "https://job-hub.bpp.io",
    "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
    "message_id": "481a01fc-4b45-4d49-9558-c6a7dfad8b75",
    "ttl": "PT10M",
    "timestamp": "2023-02-23T08:09:02.172Z"
  },
  "message": {
    "order": {
      "provider": {
        "id": "1"
      },
      "items": [
        {
          "id": "a23f2fdfbbb8ac402bf259d75402eb0792f50c095f7d08a55475e7af1c2dadca",
          "fulfillment_ids": [
            "1"
          ]
        }
      ],
      "fulfillments": [
        {
          "id": "1",
          "customer": {
            "person": {
              "name": "Sanjay",
              "gender": "Male",
              "age": "35",
              "skills": [
                {
                  "code": "Android",
                  "name": "Android"
                },
                {
                  "code": "AWS",
                  "name": "AWS"
                }
              ],
              "languages": [
                {
                  "code": "en",
                  "name": "english"
                },
                {
                  "code": "ml",
                  "name": "Malayalam"
                },
                {
                  "code": "hi",
                  "name": "Hindi"
                }
              ],
              "tags": [
                {
                  "code": "current-experience",
                  "list": [
                    {
                      "descriptor": {
                        "code": "exp-years",
                        "name": "Experience"
                      },
                      "value": "P4Y2M"
                    },
                    {
                      "descriptor": {
                        "code": "current-company",
                        "name": "Current Company"
                      },
                      "value": "ABC tech"
                    }
                  ]
                },
                {
                  "code": "salary-details",
                  "list": [
                    {
                      "descriptor": {
                        "code": "expected-salary",
                        "name": "Expected Salary"
                      },
                      "value": "80000"
                    },
                    {
                      "descriptor": {
                        "code": "current-salary",
                        "name": "Current Salary"
                      },
                      "value": "50000"
                    }
                  ]
                },
                {
                  "code": "documents",
                  "list": [
                    {
                      "descriptor": {
                        "code": "resume",
                        "name": "resume"
                      },
                      "value": "https://link-to-the-document.com"
                    }
                  ]
                }
              ]
            },
            "contact": {
              "phone": "9999999999999",
              "email": "abc@abc.bc"
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
      ]
    }
  }
}
```

</details>

8. BPP sends confirmation of submission of job application.

<details>

<summary>On Confirm API</summary>

```json
{
    "context": {
        "domain": "onest:work-opportunities",
        "action": "on_confirm",
        "version": "1.1.0",
        "bap_id": "worker-hub.bap.io",
        "bap_uri": "https://worker-hub.bap.io",
        "bpp_id": "job-hub.bpp.io",
        "bpp_uri": "https://job-hub.bpp.io",
        "transaction_id": "a9aaecca-10b7-4d19-b640-b047a7c62195",
        "message_id": "8cbb5e99-5d06-4855-81e9-a4fc8013dbff",
        "timestamp": "2023-02-23T08:20:06.0674501+00:00",
        "ttl": "P1M"
    },
    "message": {
        "order": {
            "id": "1677140405881",
            "provider": {
                "id": "1",
                "descriptor": {
                    "name": "Affinidi"
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
                    }
                ]
            },
            "items": [
                {
                    "id": "a23f2fdfbbb8ac402bf259d75402eb0792f50c095f7d08a55475e7af1c2dadca",
                    "descriptor": {
                        "name": "Fullstack Engineer",
                        "long_desc": "We’re on a search for a Staff Mobile Developer with the following attributes: Critical Thinking- You are able to skillfully conceptualise, apply, analyse and evaluate information gathered from observation, experience or communication and use it as a guide to action Data-Driven attitude — You often propose solutions or make a point in a logical and objective manner, substantiated with accurate data and evidence Dealing with Ambiguity — You can effectively cope with change and uncertainty, and are comfortable when things are up in the air Goal-oriented — You are driven and can be counted on to exceed goals. You steadfastly push yourself and others to achieve results all the time Problem Solving — You can easily identify and solve complex problems in a methodological manner "
                    },
                    "fulfillment_ids": [
                        "1"
                    ],
                    "location_ids": [
                        "L1"
                    ],
                    "time": {
                        "range": {
                            "start": "2023-01-03T13:23:01+00:00",
                            "end": "2023-02-03T13:23:01+00:00"
                        }
                    },
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
                        },
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
                        },
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
                        },
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
                        },
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
            ],
            "fulfillments": [
                {
                    "id": "1",
                    "type": "REMOTE",
                    "customer": {
                        "person": {
                            "name": "Sanjay",
                            "gender": "Male",
                            "age": "35",
                            "skills": [
                                {
                                    "code": "Android",
                                    "name": "Android"
                                },
                                {
                                    "code": "AWS",
                                    "name": "AWS"
                                }
                            ],
                            "languages": [
                                {
                                    "code": "en",
                                    "name": "english"
                                },
                                {
                                    "code": "ml",
                                    "name": "Malayalam"
                                },
                                {
                                    "code": "hi",
                                    "name": "Hindi"
                                }
                            ],
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
                                },
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
                        },
                        "contact": {
                            "phone": "9999999999999",
                            "email": "abc@abc.bc"
                        }
                    }
                }
            ]
        }
    }
}
```

</details>

9. BAP can use the status API to fetch the job application.

#### Status API

```json
{
  "context": {
    "domain": "onest:financial-support",
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
      "id": "1677140405881"
    }
  }
}
```

12. BPP send the on\_status request, with job application status.

#### On Status API

```json
{
    "context": {
    "domain": "onest:financial-support",
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
            "id": "1677140405881",
            "provider": {
                "id": "1",
                "descriptor": {
                    "name": "Affinidi"
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
                    }
                ]
            },
            "items": [
                {
                    "id": "a23f2fdfbbb8ac402bf259d75402eb0792f50c095f7d08a55475e7af1c2dadca",
                    "descriptor": {
                        "name": "Fullstack Engineer",
                        "long_desc": "We’re on a search for a Staff Mobile Developer with the following attributes: Critical Thinking- You are able to skillfully conceptualise, apply, analyse and evaluate information gathered from observation, experience or communication and use it as a guide to action Data-Driven attitude — You often propose solutions or make a point in a logical and objective manner, substantiated with accurate data and evidence Dealing with Ambiguity — You can effectively cope with change and uncertainty, and are comfortable when things are up in the air Goal-oriented — You are driven and can be counted on to exceed goals. You steadfastly push yourself and others to achieve results all the time Problem Solving — You can easily identify and solve complex problems in a methodological manner "
                    },
                    "fulfillment_ids": [
                        "1"
                    ],
                    "location_ids": [
                        "L1"
                    ],
                    "time": {
                        "range": {
                            "start": "2023-01-03T13:23:01+00:00",
                            "end": "2023-02-03T13:23:01+00:00"
                        }
                    },
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
                        },
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
                        },
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
                        },
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
                        },
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
            ],
            "fulfillments": [
                {
                    "id": "1",
                    "type": "REMOTE",
                    "state": {
                        "descriptor": {
                            "code": "OFFER-EXTENDED",
                            "name": "Offer Extended"
                        },
                        "updated_at": "2023-02-06T09:55:41.161Z"
                    },
                    "customer": {
                        "person": {
                            "name": "Sanjay",
                            "gender": "Male",
                            "age": "35",
                            "skills": [
                                {
                                    "code": "Android",
                                    "name": "Android"
                                },
                                {
                                    "code": "AWS",
                                    "name": "AWS"
                                }
                            ],
                            "languages": [
                                {
                                    "code": "en",
                                    "name": "english"
                                },
                                {
                                    "code": "ml",
                                    "name": "Malayalam"
                                },
                                {
                                    "code": "hi",
                                    "name": "Hindi"
                                }
                            ],
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
                                },
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
                        },
                        "contact": {
                            "phone": "9999999999999",
                            "email": "abc@abc.bc"
                        }
                    }
                }
            ]
        }
    }
}
```
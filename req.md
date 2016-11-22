FORMAT: 1A

# DINA API Guidelines
This document describes the guidelines for DINA Web APIs.

The web API guidelines focus primarily on the two parts of the web API:
- the structure of the URLs, their parameters, headers: Expressed using [blueprint-api](https://apiblueprint.org/) examples
- json of requests and responses: Expressed internal to the blueprint examples, examples of request and response using [jsonapi.org](jsonapi.org)


## Media [/media/}]

### Retrieve all media entity types json document, paged [GET]




## Media [/media/{mid}]
+ Parameters

    + mid: 001196a9-abef-419e-a8b7-f0a00157c588 (required) - Unique identifier for a media type
    
### Retrieve a media object json document [GET]

+ Request JSON Message

    + Headers
            Accept: application/json
	    
+ Response 200 (application/json)

    + Body

            {
    		"comment": "json to come; jsonapi compliant",
                "mid": "001196a9-abef-419e-a8b7-f0a00157c588",
            }

+ Response 404 (application/json)

    + Body

            {
		"comment": "json to come; jsonapi compliant",
		"id": "001196a9-abef-419e-a8b7-f0a00157c588",
                "error": "uuid does not exist"
		}

###  [POST]
+ Headers
        Accept: application/json
	    
+ Response 405 (application/json)

  + Body

            {
		"comment": "json to come; jsonapi compliant",
		"id": "001196a9-abef-419e-a8b7-f0a00157c588",
                "error": "uuid does not exist"
		}


### Update a Message [PUT]

+ Headers
        Accept: application/json
+ Request Update media type (application/json)

                {
		"comment": "json to come; jsonapi compliant",
		}

+ Response 200

    + Body
                {
		"comment": "json to come; jsonapi compliant",
		}

### Retrieve only meta-data section for corresponding GET request [HEAD]

+ Headers
        Accept: application/json
+ Request Update media type (application/json)

+ Response 200

    + Body
                {
		"comment": "json to come; jsonapi compliant",
		}




## Media [/media/count}]
### Retrieve count of all media entity types json document, paged [GET]
+ Request JSON Message

    + Headers
            Accept: application/json
	    
+ Response 200 (application/json)

    + Body

            {
    		"comment": "json to come; jsonapi compliant",
                "count": 12,
            }

## Media [/media/{mid}/{id}]
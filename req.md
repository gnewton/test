FORMAT: 1A

# Requests API
Following the [Responses](05.%20Responses.md) example, this API will show you
how to define multiple requests and what data these requests can bear. Let's
demonstrate multiple requests on a trivial example of content negotiation.

## API Blueprint
+ [Previous: Responses](05.%20Responses.md)
+ [This: Raw API Blueprint](https://raw.github.com/apiaryio/api-blueprint/master/examples/06.%20Requests.md)
+ [Next: Parameters](07.%20Parameters.md)

# Group Messages
Group of all messages-related resources.

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
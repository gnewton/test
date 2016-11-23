FORMAT: 1A

# DINA API Guidelines
This document describes the guidelines for DINA Web APIs.

The web API guidelines focus primarily on the two parts of the web API:
- the structure of the URLs, their parameters, headers: Expressed using [blueprint-api](https://apiblueprint.org/) examples
- json of requests and responses: Expressed internal to the blueprint examples, examples of request and response using [jsonapi.org](jsonapi.org)

#jsonapi
Web service json must adhere to the jsonapi standard v1.0, with the following exception:
- In the section http://jsonapi.org/format/#crud-creating the datandard indicates:
"The response MUST also include a document that contains the primary resource created.".
For large media objects, moving extremely large data from the server back to the client after submission would be prohibitive from the bandwidth perspective.

Only jsonapi links and data are used. 

## Media [/media/}]

### Retrieve all media entity types json document, paged [GET]
+ Response 200 (application/vnd.api+json)

    + Body
    
            {
               "links":{
                  "self":"http://dina.org/media"
               },
               "data":[
                  {
                     "type":"media",
                     "id":"1",
                     "attributes":{
                        "type":"images"
                     }
                  },
                  {
                     "type":"media",
                     "id":"2",
                     "attributes":{
                        "type":"video"
                     }
                  }
               ]
            }


## Media [/media/{mid}]
+ Parameters
    + mid: images (required) - Unique identifier for a media type

### Retrieve a media type [GET]

+ Request JSON Message

    + Headers
            Accept: application/vnd.api+json
	    
+ Response 200 (application/vnd.api+json)

    + Body

            {
               "links":{
                  "self":"http://dina.org/media/{mid}"
               },
               "data":[
                  {
                     "type":"image",
                     "id":"001196a9-abef-419e-a8b7-f0a00157c588",
                     "attributes":{
                        "content_base64":"TWFuIGlzIGRpc3Rpbmd1aXNoZWQsIG5vdCBvbmx5IGJ5IGhpcyByZWFzb24sIGJ1dCBieSB0aGlzIHNpbmd1bGFyIHBhc3Npb24gZnJvbSBvdGhlciBhbmltYWxzLCB3aGljaCBpcyBhIGx1c3Qgb2YgdGhlIG1pbmQsIHRoYXQgYnkgYSBwZXJzZXZlcmFuY2Ugb2YgZGVsaWdodCBpbiB0aGUgY29udGludWVkIGFuZCBpbmRlZmF0aWdhYmxlIGdlbmVyYXRpb24gb2Yga25vd2xlZGdlLCBleGNlZWRzIHRoZSBzaG9ydCB2ZWhlbWVuY2Ugb2YgYW55IGNhcm5hbCBwbGVhc3VyZS4="
                     }
                  }
               ]
            }

+ Response 404 (application/vnd.api+json)

    + Body

           {
             "errors": [
               {
                 "status": "404",
                 "title":  "id does not exist",
		 "source": { "parameter": "id" },
               }
             ]
           }


###  [POST]
+ Headers
        Accept: application/vnd.api+json
	    
+ Response 405 (application/vnd.api+json)

  + Body
  
            {
              "comment": "json to come; jsonapi compliant",
            "id": "001196a9-abef-419e-a8b7-f0a00157c588",
            "error": "uuid does not exist"
            }


### Update a Message [PUT]

+ Headers
        Accept: application/vnd.api+json
+ Request Update media type (application/vnd.api+json)

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
        Accept: application/vnd.api+json
+ Request Update media type (application/vnd.api+json)

+ Response 200

    + Body

	{
		"comment": "json to come; jsonapi compliant",
		}




## Media [/media/count}]
### Retrieve count of all media entity types json document, paged [GET]
+ Request JSON Message

    + Headers
            Accept: application/vnd.api+json
	    
+ Response 200 (application/vnd.api+json)

    + Body

            {
    		"comment": "json to come; jsonapi compliant",
                "count": 12,
            }


## Media [/media/{mid}]
### Retrieve all items of type {mid}, paged [GET]
+ Response 200 (application/vnd.api+json)

    + Body

            {
               "links":{
                  "self":"http://dina.org/media/images"
		  next": "http://dina.org/media/images?page[offset]=2&page[limit]=2",
                 "last": "http://dina.org/media/images?page[offset]=967&page[limit]=2"
               },
               "data":[
                  {
                     "type":"image",
                     "id":"001196a9-abef-419e-a8b7-f0a00157c588",
                     "attributes":{
                        "content_base64":"TWFuIGlzIGRpc3Rpbmd1aXNoZWQsIG5vdCBvbmx5IGJ5IGhpcyByZWFzb24sIGJ1dCBieSB0aGlzIHNpbmd1bGFyIHBhc3Npb24gZnJvbSBvdGhlciBhbmltYWxzLCB3aGljaCBpcyBhIGx1c3Qgb2YgdGhlIG1pbmQsIHRoYXQgYnkgYSBwZXJzZXZlcmFuY2Ugb2YgZGVsaWdodCBpbiB0aGUgY29udGludWVkIGFuZCBpbmRlZmF0aWdhYmxlIGdlbmVyYXRpb24gb2Yga25vd2xlZGdlLCBleGNlZWRzIHRoZSBzaG9ydCB2ZWhlbWVuY2Ugb2YgYW55IGNhcm5hbCBwbGVhc3VyZS4="
                     },
		     {
                     "type":"image",
                     "id":"778867a9-aaaa-419e-a8b7-f0a00157c588",
                     "attributes":{
                        "content_base64":"BpcyBhIGx1c3Qgb2YgdGhlIG1pbmQsIHRoYXQgYnkgYSBwZXJzZXZlcmFuY2Ugb2YgZGVsaWdodCBpbiB0aGUgY29udGludWVkIGFuZCBpbmRlZmF0aWdhYmxlIGdlbmVyYXRpb24gb2Yga25vd2xlZGdlLCBleGNlZWRzIHRoZSBzaG9ydCB2ZWhlbWVuY2Ugb2YgYW55IGNhcm5hbCBwbGVhc3VyZS4TWFuIGlzIGRpc3Rpbmd1aXNoZWQsIG5vdCBvbmx5IGJ5IGhpcyByZWFzb24sIGJ1dCBieSB0aGlzIHNpbmd1bGFyIHBhc3Npb24gZnJvbSBvdGhlciBhbmltYWxzLCB3aGljaC="
                     }
                  }
               ]
            }




###  [POST]
+ Headers
        Accept: application/vnd.api+json

+ Request Add one or more items of entity type {mid} (application/vnd.api+json)

+ Response 201 (application/vnd.api+json)

+ Body

		{
		"comment": "json to come; jsonapi compliant",
		}


## Media [/media/{mid}/count]
### Count of items of media type {mid} [GET]
+ Headers
        Accept: application/vnd.api+json

+ Request Add one or more items of entity type {mid} (application/vnd.api+json)

+ Response 200 (application/vnd.api+json)

+ Body

		{
		"comment": "json to come; jsonapi compliant",
		"count": 3827
		}


==================================================================

## Media [/media/{mid}/{id}]
+ Parameters
    + mid: images (required) - Unique identifier for a media type
    + id: 001196a9-abef-419e-a8b7-f0a00157c588 (required) - Unique identifier for a media object of type {mid}

### Retrieve a single item of type {mid} with unique identifier {id} [GET]

+ Request JSON Message

    + Headers
            Accept: application/vnd.api+json
	    
+ Response 200 (application/vnd.api+json)

    + Body

            {
               "links":{
                  "self":"http://dina.org/media/{mid}"
               },
               "data":[
                  {
                     "type":"image",
                     "id":"001196a9-abef-419e-a8b7-f0a00157c588",
                     "attributes":{
                        "content_base64":"TWFuIGlzIGRpc3Rpbmd1aXNoZWQsIG5vdCBvbmx5IGJ5IGhpcyByZWFzb24sIGJ1dCBieSB0aGlzIHNpbmd1bGFyIHBhc3Npb24gZnJvbSBvdGhlciBhbmltYWxzLCB3aGljaCBpcyBhIGx1c3Qgb2YgdGhlIG1pbmQsIHRoYXQgYnkgYSBwZXJzZXZlcmFuY2Ugb2YgZGVsaWdodCBpbiB0aGUgY29udGludWVkIGFuZCBpbmRlZmF0aWdhYmxlIGdlbmVyYXRpb24gb2Yga25vd2xlZGdlLCBleGNlZWRzIHRoZSBzaG9ydCB2ZWhlbWVuY2Ugb2YgYW55IGNhcm5hbCBwbGVhc3VyZS4="
                     }
                  }
               ]
            }

+ Response 404 (application/vnd.api+json)

    + Body

            {
		"comment": "json to come; jsonapi compliant",
		"mid": "images",
		"id": "001196a9-abef-419e-a8b7-f0a00157c588",
	    	"error": "id does not exist"
		}

### Update a Message [PUT]

+ Headers
        Accept: application/vnd.api+json
+ Request Update media type (application/vnd.api+json)

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
        Accept: application/vnd.api+json
+ Request Update media type (application/vnd.api+json)

+ Response 200

    + Body
                {
		"comment": "json to come; jsonapi compliant",
		}










## Media [/media/{mid}?minid=1000&maxid=2000}]
Get a range of items of type {mid}.


+ Parameters
    + minid: internal key identifier, min value
    + maxid: internal key identifier, max value

### Retrieve first page of paged list of all matching data objects of type image, within id range 1000-2000, starting at OFFSET=0 and LIMIT=defaultLimitSize. [GET]
+ Headers
        Accept: application/vnd.api+json

+ Response 200

    + Body
                {
		"comment": "json to come; jsonapi compliant",
		}





## Media [/media/{mid}?search_field=taxon&search=Thaumotopea]
Text search of one of the {mid} object's fields. 

+ Parameters
    + search_field: the field of the item to be searched
    + search: the term or regex search

### Retrieve first page of paged list of all matching data objects of type image, within id range 1000-2000, starting at OFFSET=0 and LIMIT=defaultLimitSize. [GET]
+ Headers
        Accept: application/vnd.api+json

+ Response 200

    + Body
                {
		"comment": "json to come; jsonapi compliant",
		}

+ Response 400

    + Body
                {
		"comment": "json to come; jsonapi compliant",
		"error": "field 'foo' does not exist",
		}

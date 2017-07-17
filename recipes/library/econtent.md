# e-content viewed statement template

## Notes for next call

- Headers given by Lee and notes
- no proposed new iris have been placed into vocab yet

This statement template is in draft. 
Based on generic template statement: [Viewed](/generic/view.md)

[Statement Template Changes](/version_changes.md#econtent)

## Purpose
This template defines the structure and terms to record the experience of viewing a reading list

### Actor
Common entity identifier:  ActorA, as defined on the [common structures](/common_structures.md#actora) page.

The actor entity describes the individual that is accessing econtent.

### Example:

``` Javascript
{
    "version": "1.0.0",
    "actor": {
        "objectType": "Agent",
        "name": "John Smith#",
        "account": {
            "name": "john-smith",
            "homePage": "http://ezproxy.jisc.ac.uk"
        }
    },
```

### Verb
Common entity identifier: VerbA, as defined on the [common structures](/common_structures.md#verba) page.

The Verb,[viewed](/vocabulary.md#verbs) denotes the action of the user's browser or app requesting the econtent.

### Example:

``` javascript
"verb": {
        "id": "http://id.tincanapi.com/verb/viewed",
        "display": {
            "en": "viewed"
        }
    },
```


### Timestamp
An ISO 8601 format timestamp that corresponds to the time of when the content was accessed.

### Example:

``` javascript
"timestamp": "2015-09-18T01:54:51.484Z",
```

### Result
The result entity containts the http response code


### Example

``` javascript
"result":{
"completion": COMPLETED,
"response": "HTTP_RESPONSE"
},
``` 

### Object



### Example

``` javascript
"object": {
	"objectType": "Activity",
	"id": "http://onlinelibrary.jisc.ac.uk/doi/10.1111"   	 	
	"definition": {
		"type": "http://id.tincanapi.com/activitytype/resource",			
		"name": { "en": "The Condition of the Working Class in England" },			   
	 }
	 "extensions": {
     		 "http://xapi.jisc.ac.uk/subType": "http://xapi.jisc.ac.uk/externalURL"
	 }
    }
}
```





### Context
Common entity identifier:



### Example:

``` javascript
 "context": {
		"platform": "UxAPI",
		"extensions": {
			"http://xapi.jisc.ac.uk/sessionId": "SESSION_ID",
			"http://id.tincanapi.com/extensions/ip-address": "IP",
			"http://id.tincanapi.com/extension/referrer": "HTTP_REFERRER",
			"http://id.tincanapi.com/extension/browser-info": "HTTP_BROWSER_INFO",
			"http://xapi.jisc.ac.uk/version": "1.0"
		}
	}
}
```


## Full Example

{
	"version": "1.0.0",
	"actor": {
		"objectType": "Agent",
		"account": {
			"name": "UNAME",
			"homePage": "HOMEPAGE"
		}
	},
	"timestamp": "TIMESTAMP",
	"verb": {
		"id": "http://id.tincanapi.com/verb/viewed",
		"display": {
			"en": "viewed"
		}
	},
	"result": {
		"completion": "COMPLETED",
		"response": "HTTP_RESPONSE"
	},
	"object": {
		"objectType": "Activity",
		"id": "HTTP_URL",
		"definition": {
			"type": "http://id.tincanapi.com/activitytype/resource",
			"name": {
				"en": "eResource"
			},
			"description": {
				"en": "an eResource made available via a proxy service"
			}
		}
	},
	"context": {
		"platform": "UxAPI",
		"extensions": {
			"http://xapi.jisc.ac.uk/sessionId": "SESSION_ID",
			"http://id.tincanapi.com/extensions/ip-address": "IP",
			"http://id.tincanapi.com/extension/referrer": "HTTP_REFERRER",
			"http://id.tincanapi.com/extension/browser-info": "HTTP_BROWSER_INFO",
			"http://xapi.jisc.ac.uk/version": "1.0"
		}
	}
}

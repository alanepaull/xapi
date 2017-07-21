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
Common entity identifier: ObjectA

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

<table>
	<tr><th>Property [cardinality]</th><th>Description</th><th>Value information</</th></tr>
	<tr>
		<td>context.platform [1]</td>
		<td>The platform used in the experience of this learning activity. The value used should not change between platform upgrades and version changes and should typically be a concise name by which the application is commonly known</td>
		<td>string</td>
	</tr>	
	<tr>
		<td>context.extensions.version [0..1]</td>
		<td>Recommended, identifies the version of the Jisc xAPI profile found on the ReadMe page. <br/></td>
		<td>decimal</td>
	</tr>
	<tr>
		<td>context.extension.sessionId [0..1]</td>
		<td>The VLE session ID, or a suitably hashed version of it. A value should be provided if this information is available.</td>
		<td>string</td>
	<tr> 
		<td>context.extension.ip-address [1]</td>
		<td>client's IP address. An IPv4 address is recommended.</td>
		<td>ip address</td>
	<tr> 
		<td>context.extension.referrer [0..1]</td>
		<td>refering url</td>
		<td>URL</td>
	<tr> 
	<tr> 
		<td>context.extension.browser_info [0..1]</td>
		<td></td>
		<td></td>
	<tr> 
</table>

### Example:

``` javascript
 "context": {
		"platform": "UxAPI",
		"extensions": {
			"http://xapi.jisc.ac.uk/sessionId": "SESSION_ID",
			"http://id.tincanapi.com/extensions/ip-address": "IP",
			"http://id.tincanapi.com/extension/referrer": "HTTP_REFERRER",
			"http://id.tincanapi.com/extension/browser-info": "HTTP_BROWSER_INFO",
			"http://xapi.jisc.ac.uk/version": "x-ignore"
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
			"http://xapi.jisc.ac.uk/version": "x-ignore"
		}
	}
}

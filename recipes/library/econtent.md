# e-content viewed statement template

## Notes for next call

- Headers given by Lee and notes
- no proposed new iris have been placed into vocab yet

client_ip  (context)

username_if_obtained_from_identd (usually '-')  (What do we do with usernames, is there some kind of mapping to vle usernames?)

username_if_obtained_via_other_means  (What do we do with usernames, is there some kind of mapping to vle usernames?)

session_id (in context)

timestamp (in timestamp entity)

http_request (this is the object, but we need a conversation about type and subtype - I don't know what we know about the type etc)

http_response_code (created an extension for this, but could this go in result?)

bytes_downloaded (is this useful?)

http_referrer (context)

http_browser_info (is this keypairs like http://id.tincanapi.com/extension/browser-info )

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


### Object



### Example

``` javascript
"object": {
	"objectType": "Activity",
	"id": "http://onlinelibrary.jisc.ac.uk/doi/10.1111"   	 	
	"definition": {
		"type": "http://xapi.jisc.ac.uk/eContent",			
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
  "platform": "Ezproxy", // I'm not sure that ezproxy is actually the service.
  "extensions": {
	"http://xapi.jisc.ac.uk/sessionId": "32456891",
    "http://id.tincanapi.com/extensions/ip-address": "10.3.3.48",
    "http://xapi.jisc.ac.uk/version" : "1.0"
	"http://id.tincanapi.com/extension/browser-info" :  { "code_name": "Mozilla", "name": "Netscape", "version": "5.0 (Macintosh; Intel Mac OS X 10_9_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/33.0.1750.152 Safari/537.36", "platform": "MacIntel", "user-agent-header": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/33.0.1750.152 Safari/537.36", "cookies-enabled": true }
	"http://id.tincanapi.com/extension/referrer" : "http://moodle.data.alpha.jisc.ac.uk/mod/page"
	"http://xapi.jisc.ac.uk/responseCode" : "200"
  }
}
```




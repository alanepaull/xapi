# mobile_app_content_viewed statement template

Based on generic template statement: [Viewed](/generic/view.md)

[Statement Template Changes](/version_changes.md#mobile-app-content-viewed)

## Purpose
This recipe defines the structure and terms to record the experience of viewing a mobile app screen. It shares a lot with vle_resource_viewed.

### Actor
Common entity identifier: [ActorA](/common_structures.md#actora)

### Entity Example:
The actor entity describes the individual that is viewing a vle resource.


``` Javascript
    "actor": {
        "objectType": "Agent",
        "name": "John Smith",
        "account": {
            "name": "jsmith12",
            "homePage": "https://courses.alpha.jisc.ac.uk/moodle"
        }

```

### Verb
Common entity identifier: [VerbA](/common_structures.md#verba)

The verb [viewed](/vocabulary.md#viewed) denotes the action of the user's browser or app requesting the resource that the user wishes to view.

### Example:

``` javascript
"verb": {
        "id": "http://id.tincanapi.com/verb/viewed",
        "display": {
            "en": "viewed"
        }
    },
```
### Context
Common entity identifier: [ContextA](/common_structures.md#contexta) page.

### Example:

``` javascript
"context": {
        "platform": "Study-Goal",
        "extensions": {
					
		  	"http://xapi.jisc.ac.uk/sessionId": "32456891"  ,
		  	"http://id.tincanapi.com/extension/ip-address": "10.3.3.48",
			"http://xapi.jisc.ac.uk/version" : "1.0"
			
			}
              
        }
```

### Object

Common entity identifier: [ObjectA](/common_structures.md#objecta) 

For this recipe the courseArea is optional, but should use uddModInstanceID when present. See the [vocabularies](/vocabulary.md#42-coursearea-properties) page for more information.

In this recipe the object should identify what was viewed. A list of valid values  for the object definition type can be found in the [vocab page](/vocabulary.md#Object.definition.extension)

### Example

``` javascript
"object": {
  "objectType": "Activity",
  "id": "https://jisc.ac.uk/studygoal/stats",
  "definition": {
    "type": "http://activitystrea.ms/schema/1.0/application",
    "name": {
      "en": "University of Jisc Study Goal"
    },
    "extensions": {
      "http://xapi.jisc.ac.uk/subType": "http://id.tincanapi.com/activitytype/mobile-app",
      "http://xapi.jisc.ac.uk/courseArea": {
		"http://xapi.jisc.ac.uk/uddModInstanceID": "LA101-200-2016S1-0"
	}
    }
  }
}
```

### Statement Example

``` javascript
{
	"version": "1.0.0",
	"actor": {
		"objectType": "Agent",
		"name": "John Smith",
		"account": {
			"name": "2",
			"homePage": "https://jisc.ac.uk"
		}
	},

	"verb": {
		"id": "http://id.tincanapi.com/verb/viewed",
		"display": {
			"en": "viewed"
		}
	},
	"context": {
		"platform": "Study-Goal",
		"extensions": {
			"http://xapi.jisc.ac.uk/sessionId": "32456891",
			"http://id.tincanapi.com/extension/ip-address": "10.3.3.48",
			"http://xapi.jisc.ac.uk/version": "1.0"
		}

	},

	"object": {
		"objectType": "Activity",
		"id": "https://jisc.ac.uk/studygoal/stats",
		"definition": {
			"type": "http://activitystrea.ms/schema/1.0/application",
			"name": {
				"en": "University of Jisc Study Goal"
			},
			"extensions": {
				"http://xapi.jisc.ac.uk/subType": "http://id.tincanapi.com/activitytype/mobile-app",
				"http://xapi.jisc.ac.uk/courseArea": {
					"http://xapi.jisc.ac.uk/uddModInstanceID": "LA101-200-2016S1-0"
			}
		}
	}
}
``` 

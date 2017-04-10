# mobile_app content viewed recipe
Revision: 1.3

## Purpose
This recipe defines the structure and terms to record the experience of viewing a mobile app screen. It shares a lot with vle_resource_viewed.

### Actor
Common entity identifier:  ActorA, as defined on the [common structures](../common_structures.md#actora) page.

The actor entity describes the individual that is viewing a vle resource.

### Example:

``` Javascript
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
```

### Verb
Common entity identifier: VerbA, as defined on the [common structures](../common_structures.md#verba) page.

The Verb,[viewed](/vocabulary.md#verbs) denotes the action of the user's browser or app requesting the resource that the user wishes to view.

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
Common entity identifier: ContextA, as defined on the [common structures](../common_structures.md#contextc) page.

### Example:

``` javascript
"context": {
        "platform": "Study-Goal",
        "extensions": {
					
		  	"http://xapi.jisc.ac.uk/sessionId": "32456891"  ,
		  	"http://id.tincanapi.com/extension/ip-address": "10.3.3.48",
			"http://xapi.jisc.ac.uk/recipeVersion" : "mobile_app_content_viewedV1.0"
			
			}
              
        }
```

### Object

Common entity identifier: ObjectA, as defined on the [common structures](../common_structures.md#objecta) page.

For this recipe the courseArea is optional, but should use uddModInstanceID when present. See the [vocabularies](../vocabulary.md#42-coursearea-properties) page for more information

For this recipe the object needs to identify what was viewed. A list of valid values  for the object definition type can be found at (../vocabulary.md#Object.definition.extension)

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
      "http://xapi.jisc.ac.uk/uddModInstanceID" : "2016.sem1.psy101"
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
			"http://xapi.jisc.ac.uk/recipeVersion": "mobile_app_content_viewedV1.0"
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
				"http://xapi.jisc.ac.uk/uddModInstanceID": "2016.sem1.psy101"
			}
		}
	}
}
``` 

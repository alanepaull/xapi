# vle_gradebook_viewed statement template
Revision: 1.3

##Purpose
This template defines the structure and terms to record the experience of viewing a gradebook

### Actor
Common entity identifier:  ActorA, as defined on the [common structures](/common_structures.md#actora) page.

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
            "homePage: "https://courses.alpha.jisc.ac.uk/moodle"
        }
    },
```

### Verb
Common entity identifier: VerbA, as defined on the [common structures](/common_structures.md#verba) page.

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
Common entity identifier: ContextA, as defined on the [common structures](/common_structures.md#contextc) page.

### Example:

``` javascript
"context": {
        "platform": "Moodle",
        "extensions": {
	

					
		  	"http://xapi.jisc.ac.uk/sessionId": "32456891"  ,
		  	"http://id.tincanapi.com/extension/ip-address": "10.3.3.48"
			"http://xapi.jisc.ac.uk/recipeVersion" : "vle_resource_viewedV1.3"
			
			}
              
        }
```

### Object

Common entity identifier: ObjectA, as defined on the [common structures](/common_structures.md#objecta) page.

For this recipe the object needs to identify what was viewed. A list of valid values  for the object definition type can be found at (../vocabulary.md#Object.definition.extension)

### Example


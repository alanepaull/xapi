#vle_logged_out Recipe
Revision: 1.2

## Purpose
This activity records a user logging out of a VLE.
## Definition
### Actor
Common entity identifier:  ActorA, as defined on the [common structures](../common_structures.html#actora) page.

The actor entity describes the individual logging out of the system.

### Example
``` Javascript
{

    "actor": {
        "objectType": "Agent",
        "name": "John Smith",
        "account": {
            "name": "jsmith12",
            "homePage": "https://courses.alpha.jisc.ac.uk/moodle"
        }
    },
```

### Verb
Common entity identifier: VerbA

Common entity identifier: VerbA, as defined on the [common structures](../common_structures.html#verba) page.

This recipe uses the [logged out](/vocabulary.html#verbs) describes the action of logging out of a platform.

Example:

``` javascript
"verb": {
        "id": "https://brindlewaye.com/xAPITerms/verbs/loggedout",
        "display": {
            "en": "logged out of"
        }
    },
``` 
### Context
Common entity identifier: ContextA, as defined on the [common structures](../common_structures.html#contexta) page.

Since the logged-in action is not undertaken in the context of a learning activity or course, only the core attributes of context are applicable.

### Example:

``` javascript
"context": {
        "platform": "Moodle",
        "extensions": {
 			"http://xapi.jisc.ac.uk/sessionId":"32456891",
        	"http://id.tincanapi.com/extension/ip-address": "10.3.3.48",
			"http://xapi.jisc.ac.uk/recipeVersion" : "vle_logged_outV1.3"
			}
```

### Object
Common entity identifier: ObjectA, as defined on the [common structures](../common_structures.html#objecta) page.

For the logged-out recipe, the object.definition.type is "http://activitystrea.ms/schema/1.0/application". The subType (http://xapi.jisc.ac.uk/subType) extension should be used to identify the system type that is being logged into, in this example a Virtual Learning Environment (aka Learning Management System), identified by  http://id.tincanapi.com/activitytype/lms. Different application types should use the relevant subType, as defined on the [vocabularies](vocabulary.html#32-object-definition-extensions) page. The object.definition.name and object.definition.definition describe the resource logged out of. 


### Example
``` javascript

"object": {
        "objectType": "Activity",
        "id": "https://courses.alpha.jisc.ac.uk/moodle",
        "definition": {
            "type": "http://activitystrea.ms/schema/1.0/application",
            "name": {
                "en": "A Moodle course"
            },
            "description": {
                "en": "A Moodle course"
            },
            "extensions": {
                "http://xapi.jisc.ac.uk/subType": "http://id.tincanapi.com/activitytype/lms"
                }
            }
        },
```


### Complete VLE Specific Examples

Moodle (ToDo)

[Blackboard](/vle/blackboard/loggedout.json)

# session_timed_out statement template

## Purpose
This activity indicates the activity provider has determined that the session was abnormally terminated either by an actor or due to a system failure.

## Definition
### Actor
Common entity identifier:  ActorA, as defined on the [common structures](/common_structures.md#actora) page.

Example:
``` Javascript
{
    "actor": {
        "objectType": "Agent",
        "name": "John Smith",
        "account": {
            "name": "2",
            "homePage": "https://courses.alpha.jisc.ac.uk/moodle"
        }
    },
```

### Verb
Common entity identifier: VerbA, as defined on the [common structures](/common_structures.md#verba) page.

The Verb,[abandoned](/vocabulary.md#verbs) describes the action of logging out of a platform.

Example:

``` javascript
"verb": {
        "id": "https://w3id.org/xapi/adl/verbs/abandoned",
        "display": {
            "en": "session timed out"
        }
    },
``` 

### Context
Common entity identifier: ContextA, as defined on the [common structures](/common_structures.md#contexta) page. Only the core attributes of context are applicable.

Example:

``` javascript
"context": {
        "platform": "Moodle",
        "extensions": {
			"http://xapi.jisc.ac.uk/sessionId": "32456891",
			"http://id.tincanapi.com/extension/ip-address" :"10.3.3.48"
			"http://xapi.jisc.ac.uk/version" : "1.0"
             }
        }
```

### Object
Common entity identifier: ObjectA, as defined on the [common structures](/common_structures.md#objecta) page.

The object defines the item that the user has timed out of.  A [Jisc specific extension](common_statements.md#jisc_extensions) details that it is a VLE that is being logged out of. 

The object.definition.type is "http://activitystrea.ms/schema/1.0/application". The subType (http://xapi.jisc.ac.uk/subType) extension should be used to identify the system type that is being logged into, in this example a Virtual Learning Environment (aka Learning Management System), identified by  http://id.tincanapi.com/activitytype/lms. Different application types should use the relevant subType, as defined on the [vocabularies](vocabulary.md#32-object-definition-extensions) page.

``` javascript

"object": {
    "objectType": "Activity",
    "id": "https://courses.alpha.jisc.ac.uk/moodle",
    "definition": {
        "type": "http://activitystrea.ms/schema/1.0/application",
        "name": {
            "en": "A Moodle course"
        },
        "extensions": {
            "http://xapi.jisc.ac.uk/subType": "http://id.tincanapi.com/activitytype/lms"
        }
    }
}
```


### Complete VLE Specific Examples
Moodle (ToDo)

[Blackboard](blackboard/loggedout.json)

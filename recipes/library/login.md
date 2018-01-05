# library_system_logged_in statement template

[Statement Template Changes](/version_changes.md#library-logged-in)

## Purpose
This activity records a user logging in to a library system.

### Actor
Common entity identifier: Common entity identifier: [ActorA](/common_structures.md#actora)

#### Entity Example:
The actor entity identifies the individual that is logging in to the system.

``` Javascript
"actor": {
  "objectType": "Agent",
  "name": "John Smith",
  "account": {
    "name": "jsmith12",
    "homePage": "< dependant on system >"
  }
}
```

### Verb
Common entity identifier: [VerbA](/common_structures.md#verba)

#### Entity Example:
This verb, [logged in](/vocabulary.md#logged-in), describes the action of logging into a platform.

``` javascript
"verb": {
  "id": "https://brindlewaye.com/xAPITerms/verbs/loggedin",
  "display": {
    "en" : "logged in to"
  }
}
```

### Context
Common entity identifier: ContextA, as defined on the [common structures](/common_structures.md#contexta) page.

Since the logged-in action is not undertaken in the context of a learning activity or course, only the core attributes of context are applicable.

#### Example:
``` javascript
"context": {
  "platform": " ",
  "extensions": {
    "http://xapi.jisc.ac.uk/sessionId": "32456891",
    "http://id.tincanapi.com/extensions/ip-address": "10.3.3.48",
    "http://xapi.jisc.ac.uk/version" : "1.0"
  }
}
```

### Object
Common entity identifier: ObjectA, as defined on the [common structures](/common_structures.md#objecta) page.


#### Example:
``` javascript
"object": {
  "objectType": "Activity",
  "id": "<iri id of system> ",
  "definition": {
    "type": "<iri of system type>",
    "name": {
      "en": "< En description> "
    },
    "extensions": {
      "http://xapi.jisc.ac.uk/subType": "http://id.tincanapi.com/activitytype/lms"
    }
  }
}
```

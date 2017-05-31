# vle_logged_in statement template

Based on generic template statement: [Login](/generic/login.md)

[Statement Template Changes](/version_changes.md#logged-in)

## Purpose
This activity records a user logging in to a VLE.

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
    "homePage": "https://courses.alpha.jisc.ac.uk/moodle"
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
  "platform": "Moodle",
  "extensions": {
    "http://xapi.jisc.ac.uk/sessionId": "32456891",
    "http://id.tincanapi.com/extensions/ip-address": "10.3.3.48",
    "http://xapi.jisc.ac.uk/version" : "1.0"
  }
}
```

### Object
Common entity identifier: ObjectA, as defined on the [common structures](/common_structures.md#objecta) page.

When the object.definition.type is "http://activitystrea.ms/schema/1.0/application".  The subType (http://xapi.jisc.ac.uk/subType) extension should be used to identify the subType of the application that is being logged into, in this example a Virtual Learning Environment (aka Learning Management System), identified by  http://id.tincanapi.com/activitytype/lms. Different application types should use the relevant subType, as defined on the [vocabularies page](/vocabulary.md#32-object-definition-extensions) page.

#### Example:
``` javascript
"object": {
  "objectType": "Activity",
  "id": "https://courses.alpha.jisc.ac.uk/moodle",
  "definition": {
    "type": "http://activitystrea.ms/schema/1.0/application",
    "name": {
      "en": "University of Jisc VLE"
    },
    "extensions": {
      "http://xapi.jisc.ac.uk/subType": "http://id.tincanapi.com/activitytype/lms"
    }
  }
}
```

### Complete VLE Specific Examples
[Moodle Login Example](/vle/moodle/login.js)

[Blackboard Login Example](/vle/blackboard/loggedin.json)

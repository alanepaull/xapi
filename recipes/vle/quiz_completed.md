# quiz_assessed statement template

## Purpose

## Definition

### Actor
The actor entity is used to identify the individual that completed the quiz [ActorA](/common_structures.md#actora).

#### Entity properties:

<table>
<tr><th>Property</th><th>Description</th></tr>
<tr>
<td>actor.objectType [1]</td><td>Must have the value "Agent". Actors of type "Group" are not supported in the Jisc profile.</td>
</tr>
<tr>
<td>actor.name [0..1]</td><td>Full name of student.</td>
</tr>
<tr>
<td>	
actor.account [1] <br/>
actor.account.name [1] <br/>
actor.account.homepage [1] <br/>
</td>
<td>A JSON Object with <b>account.name</b> giving a system login id for the subject of the statement and <b>account.homepage</b> giving the URL of the home page of the application for which the login id applies.</td></tr>
</table>

### Example:

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
The verb used in quiz_assessed statement is [scored](/vocabulary.md#verbs). It describes the action of receiving an evaluation of an activity. It uses the Jisc common entity [VerbA](../common_structures.md#verba).

#### Entity properties:

<table>
	<tr><th>Property</th><th>Description</th></tr>
	<tr>
		<td>verb.id [1]</td>
		<td>An IRI that identifies the Verb. http://adlnet.gov/expapi/verbs/scored in this statement.</td>
	</tr>
	<tr>
		<td>verb.display [1]</td>
		<td>A human readable representation of Verb. It takes a RFC 5646 Language Tag. "scored" in this type of statement. </td>
	</tr>
</table>

``` javascript
"verb": {
        "id": "http://adlnet.gov/expapi/verbs/scored",
        "display": {
            "en": "scored"
        }
    },
``` 

### Result

<table>
	<tr><th>Property [cardinality]</th><th>Description</th><th>Data type</th></tr>
	<tr>
		<td>result.score.scaled [0..1]</td>
		<td>The score related to the experience as modified by scaling and/or normalization</td>
<td>decimal number between -1 and 1, inclusive.</td>
	</tr>
	<tr>
		<td>result.score.raw [0..1]</td>
		<td>Unmodified score</td>
<td>decimal number between min and max (if present, otherwise unrestricted), inclusive</td>
	</tr>
	<tr>
		<td>result.score.min [0..1]</td>
		<td>The lowest possible score</td>
<td>decimal number less than max (if present)</td>
	</tr>
	<tr>
		<td>result.score.max [0..1]</td>
		<td>The highest possible score</td>
		<td>decimal number greater than min (if present)</td>
	</tr>
	<tr>
		<td>result.completion [0..1]</td>
		<td>Indicates whether or not the Activity was completed.</td>
		<td>true or false</td>
	</tr>
	<tr>
		<td>result.response [0..1]</td>
		<td>Instructor's or automatic feedback</td>
		<td>string (256)</td>
	</tr>
	<tr>
		<td>result.duration [0..1]</td>
		<td>Durations are strings representing the amount of time something took.</td>
		<td>ISO 8601 Duration</td>
	</tr>
</table>

### Example:

```

 "result": {
      "duration": "PT9S",
      "completion": true,
      "score": {
        "max": 10,
        "raw": 1,
        "scaled": 0.1
      }
    },

````

### Object

The object identifies the quiz completed. It is based on the Jisc Profile common entity [ObjectA](../common_structures.md#objectA).

#### Entity properties:


#### Example:

``` javascript

    "object": {
	  "objectType": "Activity",
      "id": "http://localhost/moodle/mod/quiz/view.php?id=10",
		  "definition": {
			"description": {
			  "en": "A module"
			},
			"name": {
			  "en": "mquiz"
			},
			"type": "http://xapi.jisc.ac.uk/vle/quiz"
		  }
    }
		
```

### Context
Context is used to describe the module within which the quiz sits. If the device supports it, session Ids and ip-addresses can be recorded. Common entity identifier for quiz is ContextA, as defined on the [common structures](/common_structures.md#contexta) page.

#### Entity properties:


### Example:

``` javascript
"context": {
      "extensions": {
        "http://xapi,jisc.ac.uk/attempt": "Attempt 26",
        "http://xapi,jisc.ac.uk/courseArea": {
          "http://xapi.jisc.ac.uk/vle_mod_id": "Test1"
        },
        "http://id&46;tincanapi&46;com/extension/ip-address": "0:0:0:0:0:0:0:1",
        "http://xapi.jisc.ac.uk/version": "x-2017-05-16",
        "http://xapi.jisc.ac.uk/sessionId": "Iye9OqwM9O"
      },
```

## Full Example

 
    "actor": {
      "account": {
        "homePage": "http://localhost/moodle",
        "name": "stu1"
      },
      "objectType": "Agent"
    },
    "timestamp": "2017-08-10T16:37:43+02:00",
    "version": "1.0.0",
    "id": "8ff2892d-93d1-45e5-9e5b-b7e2a65305cb",
    "result": {
      "duration": "PT9S",
      "completion": true,
      "score": {
        "max": 10,
        "raw": 1,
        "scaled": 0.1
      }
    },
    "verb": {
      "display": {
        "en": "completed"
      },
      "id": "http://adlnet.gov/expapi/verbs/completed"
    },
    "object": {
      "definition": {
        "description": {
          "en": "A module"
        },
        "name": {
          "en": "mquiz"
        },
        "type": "http://xapi.jisc.ac.uk/vle/quiz"
      },
      "id": "http://localhost/moodle/mod/quiz/view.php?id=10",
      "objectType": "Activity"
    },
	"context": {
      "extensions": {
        "http://xapi.jisc.ac.uk/attempt": "Attempt 26",
        "http://xapi.jisc.ac.uk/courseArea": {
          "http://xapi.jisc.ac.uk/vle_mod_id": "Test1"
        },
        "http://id&46;tincanapi&46;com/extension/ip-address": "0:0:0:0:0:0:0:1",
        "http://xapi.jisc.ac.uk/version": "x-2017-05-16",
        "http://xapi.jisc.ac.uk/sessionId": "Iye9OqwM9O"
      },
      "platform": "Moodle"
    },
  }
}```
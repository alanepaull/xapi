# interviewed statement
Revision: 0.1 

## Purpose
This recipe records an intervention taking place. Interventions can be any learning activity, in this example an interview has taken place. The context is used to show that an intervention has taken place.

### Actor
Common entity identifier: [ActorA](../common_structures.md#actora)

#### Entity Example:

In this example it is the instructor that sends the intervention.

``` Javascript
"actor": {
	"objectType": "Agent",
      "name": "Ray Keenan",
      "account": {
         "name": "rkeenan12",
         "homePage": "http://localhost/moodle"
      }
	}
```


### Verb
Common entity identifier: [VerbA](../common_structures.md#verba)

The verb [interviewed](/vocabulary.md#verbs) denotes the action of the actor conducting an interview.


#### Entity Example:

``` javascript
"verb": {
        "id": "http://id.tincanapi.com/verb/interviewed",
        "display": {
            "en": "Interviewed"
        }
    },
```

 

### Object

Object is the person that the intervention is acted upon. It is usually the student.

``` Javascript
{
    "object": {
        "objectType": "Agent",
        "name": "John Smith",
        "account": {
            "name": "2",
            "homePage": "https://courses.alpha.jisc.ac.uk/moodle"
        }
    },
```

### Context

Common entity identifier: Context*

#### Entity Example:

context includes the version number of this recipe. 

If the activity is part of an intervention, tracked by an intervention system, the following properties may be set (Optional):

context.contextActivies is of type category.  Is tells us that this statement is related to intervention activities. 
context.extensions.interventionId is any id or ticket number used by the system to identify the intervention this was a part of.
context.extension.logplatform details the system which logged the activity.

``` javascript
"context": {
	"contextActivities":{
		"category": [{
			"objectType": "Activity",
			"id": "http://xapi.jisc.ac.uk/activities/intervention"
		}],
	},

	"extensions": {
		"http://xapi.jisc.ac.uk/recipeVersion" : "intervention.1",
		"http://xapi.jisc.ac.uk/interventionId":"38223",
		}
```

### Example


``` javascript

{
    "actor": {
        "objectType": "Agent",
        "name": "Ray Keenan",
        "account": {
            "name": "rkeenan12",
            "homePage": "http://localhost/moodle"
        }
    },
    "verb": {
        "id": "http://id.tincanapi.com/verb/interviewed",
        "display": {
            "en": "Interviewed"
        }
    },
    "object": {
        "objectType": "Agent",
        "name": "John Smith",
        "account": {
            "name": "2",
            "homePage": "https://courses.alpha.jisc.ac.uk/moodle"
        }
    },
    "context": {
        "contextActivities": {
            "category": [
                {
                    "objectType": "Activity",
                    "id": "http://xapi.jisc.ac.uk/activities/intervention"
                }
            ]
        },
        "extensions": {
            "http://xapi.jisc.ac.uk/recipeVersion": "intervention.1",
            "http://xapi.jisc.ac.uk/interventionId": "38223",
            "http://xapi.jisc.ac.uk/logPlatform": "Student Information Desk"
        }
    },
    "id": "12345678-1234-5678-1234-567812345678"
}
``` 

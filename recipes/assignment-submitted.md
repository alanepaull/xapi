---
layout: home
---

#vle_assignment_submitted Recipe
Revision: 1.3

## Purpose
This activity records a user submitting an assignment
## Definition

### Actor
Common entity identifier:  ActorA, as defined on the [common structures](../common_structures.html#actora) page.

The actor entity describes the individual who has submitted the assignment.

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
Common entity identifier: VerbA, as defined on the [common structures](../common_structures.html#verba) page.

The Verb, [completed](/vocabulary.html#verbs) describes the action of completing an activity - finishing in its entirety.

``` javascript
"verb": {
        "id": "http://adlnet.gov/expapi/verbs/completed",
        "display": {
            "en": "completed"
        }
    },
``` 

### Result
Common entity identifier: ResultA, as defined on the [common structures](../common_structures.html#resulta) page.


In this recipe the result entity is optional and includes completion. See [the xAPI specification for a full description of the result entity](https://github.com/adlnet/xAPI-Spec/blob/master/xAPI-Data.html#result)

``` javascript
 "result":{
        "completion":true
    }
```

### Object
Common entity identifier: ObjectB, as defined on the [common structures](../common_structures.html#objectb) page.


Example:

``` javascript

"object":{
		"objectType":"Activity",
		"id":"http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4",
		"definition":{
			"type":"http://adlnet.gov/expapi/activities/assessment",
			"name":{
				"en":"xapi Assignment"
			},
			"description":{
				"en":"xppi Assignment description"
				}
			},
			
		    "extensions":{
				"http://xapi.jisc.ac.uk/dueDate": "2016-02-05T17:59:45.000Z"
			}
			
		}
		
```


### Context
Common entity identifier: ContextB, as defined on the [common structures](../common_structures.html#contextb) page.

For the submitted recipe, the context.contextActivities is property with a ‘grouping’ that allows statements to be associated to the activity described in the object entities as part of a larger whole. Different activity types can be found on the vocabulary page.

Example:

``` javascript
"context": {
	"contextActivities":{
            "grouping":[
                {
                    "objectType":"Activity",
                    "id":"http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4",
                    "definition":{
                       
						"type": "http://xapi.jisc.ac.uk/define/vle/course"
                        "name":{
                            "en":"xAPI Basics"
                        },
                        "description":{
                            "en":"xAPI Basics course for Learning Analytics enthusiasts"
                        }
                    }
                }
            ]
        },
        
        "platform": "Moodle",
        "extensions": {
		
      		"http://xapi.jisc.ac.uk/courseArea": {
      		 	"http://xapi.jisc.ac.uk/vle_mod_id": "LA101",
                "id": http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4"
				},
			
 			"http://xapi.jisc.ac.uk/sessionId":"32456891",
            "http://id.tincanapi.com/extension/ip-address": "10.3.3.48"
			"http://xapi.jisc.ac.uk/recipeVersion" : "vle_assignment_submittedV1.3"
			}
		}
```




### Complete VLE Specific Examples
[Blackboard Assignment Submitted Example](/vle/blackboard/assignment_submitted.json)

[Moodle Assignment Submitted Example](/vle/moodle/assignment_submitted.json)

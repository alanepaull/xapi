---
layout: home
---

#vle_assignment_graded Recipe
Revision: 1.3

## Purpose
This activity records a graded assignment
## Definition
### Actor
Common entity identifier:  ActorA

Common entity identifier:  ActorA, as defined on the [common structures](../common_structures.html#actora) page.

The actor entity describes the individual whose work has been graded.

### Example:
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

The Verb, [scored](/vocabulary.html#verbs) describes the action of evaluating a learning activity.

### Example:

``` javascript
 "verb":{
        "id":"http://adlnet.gov/expapi/verbs/scored ",
        "display":{
            "en":"scored"
         }
    }
``` 

### Result
Common entity identifier: ResultB, as defined on the [common structures](../common_structures.html#resultb) page.

In the Jisc profile, the use of the result entity and any of its properties is optional. 


### Example:
``` javascript
 "result":{
        "score":{
            "raw":8
                }
        "extensions": {
        	"http://xapi.jisc.ac.uk/grade":"5 stars"
        	}
    },
```

### Object
Common entity identifier: ObjectB, as defined on the [common structures](../common_structures.html#objectb) page.

The object defines the activity that has been evaluated. [Examples of valid object.definition vocabulary on Activity objectTypes](/common_statements.html#object) can be found on the vocab page.


### Example:
``` javascript

"object":{
		"objectType":"Activity",
		"id":"http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4",
		"definition":{
			"type":"http://adlnet.gov/expapi/activities/assessment",
			"name":{
				"en":"Course Assignment"
			},
			"description":{
				"en":"Course Assignment description"
				}
			},
			"extensions":{
				"http://xapi.jisc.ac.uk/dueDate": "2016-02-05T17:59:45.000Z"
			}
		}
		
```



### Context
Common entity context: ContextB, as defined on the [common structures](../common_structures.html#contextb) page.

For the graded recipe, the context.contextActivities is property with a ‘grouping’ that allows statements to be associated to the activity described in the object entities as part of a larger whole. Different activity types can be found on the vocabulary page.

### Example

``` javascript
"context": {
	"contextActivities":{
            "grouping":[
                {
                    "objectType":"Activity",
                    "id":"http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4",
                    "definition":{
                        "type":"http://xapi.jisc.ac.uk/courseArea",
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
		
		"instructor": {
            "objectType": "Agent",
            "name": "instructor",
            "account": {
                "name": "Ray Keenan",
                "homePage": "http://localhost/moodle"
            },
        
        "platform": "Moodle"
        "extensions":  {
      		"http://xapi.jisc.ac.uk/courseArea": {
      		 	 "http://xapi.jisc.ac.uk/vle_mod_id": "LA101",
        		 "id":"http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4"
              },
			  
 			"http://xapi.jisc.ac.uk/sessionId": "32456891" ,
        	"http://id.tincanapi.com/extension/ip-address": "10.3.3.48"
			"http://xapi.jisc.ac.uk/recipeVersion" : "vle_assignment_gradedV1.2"
        }
```


### Complete VLE Specific Examples
[Blackboard Example](/vle/blackboard/asssignment_graded.json)

[Moodle Example](/vle/moodle/asssignment_graded.json)

# vle_assignment_graded statement template

[Statement Template Changes](/version_changes.md#assignment-graded)

## Purpose
This activity records a graded assignment
## Definition
### Actor
Common entity identifier:  ActorA

Common entity identifier:  ActorA, as defined on the [common structures](/common_structures.md#actora) page.

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
Common entity identifier: VerbA, as defined on the [common structures](/common_structures.md#verba) page.

The Verb, [scored](/vocabulary.md#verbs) describes the action of evaluating a learning activity.

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
Common entity identifier: ResultB, as defined on the [common structures](/common_structures.md#resultb) page.

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
Common entity identifier: ObjectB, as defined on the [common structures](/common_structures.md#objectb) page.

The object defines the activity that has been evaluated. [Examples of valid object.definition vocabulary on Activity objectTypes](/common_statements.md#object) can be found on the vocab page.


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
			"extensions":{
				"http://xapi.jisc.ac.uk/dueDate": "2016-02-05T17:59:45.000Z"
			}
		}
		
```



### Context
Common entity context: ContextB, as defined on the [common structures](/common_structures.md#contextb) page.

The context.contextActivities is property with a ‘grouping’ that allows statements to be associated to the activity described in the object entities as part of a larger whole. Different activity types can be found on the vocabulary page.

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
                    "extensions": {
     		   	 "http://xapi.jisc.ac.uk/subType": "http://id.tincanapi.com/activitytype/lms"
			}
                    }
                }
            ]
        },
		
	"instructor": {
            "objectType": "Agent",
            "name": "Ray Keenan",
            "account": {
                "name": "RKeenan",
                "homePage": "http://localhost/moodle"
            },
        
        "platform": "Moodle"
        "extensions":  {
      		"http://xapi.jisc.ac.uk/courseArea": {
				"http://xapi.jisc.ac.uk/vle_mod_id": "LA101",
				"http://xapi.jisc.ac.uk/uddModInstanceID": "LA101-200-2016S1-0",
				"id":"http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4"
              		},
			"http://xapi.jisc.ac.uk/sessionId": "32456891" ,
        	"http://id.tincanapi.com/extension/ip-address": "10.3.3.48"
			"http://xapi.jisc.ac.uk/version" : "1.0"
        }
```


### Complete VLE Specific Examples
[Blackboard Example](/vle/blackboard/asssignment_graded.json)

[Moodle Example](/vle/moodle/asssignment_graded.json)

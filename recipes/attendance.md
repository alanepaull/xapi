---
layout: home
---

#Attended learning activity
Revision: 0.2

DRAFT

##Purpose
This recipe defines the structure and terms to record a learner's attendance of an event such as a lecture or other learning activity. The expectation is that the source data will be collected by a system designed to explicitly record attendance via some action of the learner, such as swiping a card.

### Actor
Common entity identifier: [ActorA](../common_structures.html#actora)

#### Entity Example:
The actor entity describes the individual who has attended the learning activity.

``` Javascript
{
    "version": "1.0.0",
    "actor": {
        "objectType": "Agent",
        "name": "John Smith",
        "account": {
            "name": "2",
            "homePage": "https://www.poppleton.ac.uk/attendance/stu123"
        }
    },
```

### Verb

Common entity identifier: [VerbA](../common_structures.html#verba)

#### Entity Example:

The verb [attended](/vocabulary.html#verbs) denotes the action of the user's browser or app requesting the resource that the user wishes to view.

``` javascript
"verb": {
        "id": "http://adlnet.gov/expapi/verbs/attended",
        "display": {
            "en": "attended"
        }
    },
```

### Result
Common entity identifier: [ResultA](../common_structures.html#resulta)

#### Entity Example:
When set to "true", result.completion indicates that the learner attended the event. "false"indicates that the learner did not attend the event.

``` javascript
 "result":{
        "completion":true
    }
```

### Object
Common entity identifier: [ObjectC](../common_structures.html#objectc)

#### Entity Example:
The object defines the activity that has been completed. Examples of valid object.definition Activity object Types can be found in [the vocabulary](../vocabulary.html#30-object).

``` javascript

"object":{
		"objectType":"Activity",
		"id":"http://wicketkeeper.poppleton.ac.uk/modules/2016/sem1/psy101/qlecture1",
		"definition":{
			"type":"http://activitystrea.ms/schema/1.0/event",
			"name":{
				"en":"Lecture"
			},
			"description":{
				"en":"The first lecture of psychology 101"
				}
			},
			
		    "extensions":{
				"http://id.tincanapi.com/extension/datetime": "2016-02-05T10:00:00.000Z",
				"http://id.tincanapi.com/extension/duration": "PT1H30M0S"
			}
			
		}
		
```

### Context
Common entity identifier: ContextC

#### Entity Example:
Plugin specific extensions are optional and not part of the core recipe. The 'instructor' object is optional and describes the instructor who organised the learning event described in the object.

``` javascript
"context": {
	"contextActivities":{
            "grouping":[
                {
                    "objectType":"Activity",
                    "id":"http://wicketkeeper.poppleton.ac.uk/modules/2016/sem1/psy101",
                    "definition":{
                        "type":"http://adlnet.gov/expapi/activities/module",
                        "name":{
                            "en":"Psychology 101"
                        },
                        "description":{
                            "en":"Entrance course for psychology."
                        }
                        "extensions":{
                        	"http://xapi.jisc.ac.uk/uddModInstanceID" : "2016.sem1.psy101"
                        	}
                    }
                }
            ]
        },
		
		"instructor": {
            "objectType": "Agent",
            "name": "instructor",
            "account": {
                "name": "2",
                "homePage": "http://localhost/moodle"
            },
        
        "platform": "Wicketkeeper"
        "extensions":  {
      		"http://wicketkeeper.poppleton.ac.uk/extensions": {
      		 	 "http://wicketkeeper.poppleton.ac.uk/extensions/weighting": "3"
              },
			"http://xapi.jisc.ac.uk/recipeVersion" : "attendanceV0.1"
        }
```
# Attended_Learning_Event statement template

[Statement Template Changes](/version_changes.md#attendance)

## Purpose
This statement defines the structure and terms to record a learner's attendance of an event such as a lecture or other learning activity. The expectation is that the source data will be collected by a system designed to explicitly record attendance via some action of the learner, such as swiping a card, or of the teacher, such as completing an electronic register.
			

### Actor

Common entity identifier: [ActorA](/common_structures.md#actora)

#### Entity Example:
The actor entity describes the individual who has attended the event.

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

Common entity identifier: [VerbA](/common_structures.md#verba)

#### Entity Example:

The verb [attended](/vocabulary.md#attended) denotes the action of the user's browser or app requesting the resource that the user wishes to view.

``` javascript
"verb": {
        "id": "http://adlnet.gov/expapi/verbs/attended",
        "display": {
            "en": "attended"
        }
    },
```

### Result
Common entity identifier: [ResultC](/common_structures.md#resultc)

#### Entity Example:
The result.completion must be set true or false, indicating if the actor attended the event. The extension [attendance_late](/vocabulary.md#attendance-late) can be set to 1 if the actor did not attend the event on time. [Attendance_category](/vocabulary.md#attendance-category) can be used to express additional detail, for example whether lateness was extreme or condoned, or to provide the source system attendance type code (as might be recorded in a conventional paper register). 


``` javascript
 "result":{
        "completion":true,
		
	 "extensions":{
		  "http://xapi.jisc.ac.uk/attendance_late":1,
		  "http://xapi.jisc.ac.uk/attendance_category":"1",
		 }
    }
```

### Object
Common entity identifier: [ObjectD](/common_structures.md#objectd)

#### Entity Example:
The object defines a timetabled event that has been completed. Information on the timetabled event can be found in the object.extensions. See the [objectD section in the common structures document](/common_structures.md#objectd).

``` javascript

 "object": {
        "objectType": "Activity",
        "id": "http://wicketkeeper.poppleton.ac.uk/modules/2016/sem1/psy101/qlecture1",
        "definition": {
            "type": "http://xapi.jisc.ac.uk/lecture",
            "name": {
                "en": "Psychology 101 Introduction"
            },
            "description": {
                "en": "The first tutorial of psychology 101"
            },
	    "extensions": {
            	"http://xapi.jisc.ac.uk/subType": "http://xapi.jisc.ac.uk/workshop"
	    	"http://xapi.jisc.ac.uk/starttime": "2016-02-05T10:00:00.000Z",
          	"http://xapi.jisc.ac.uk/endtime": "2016-02-05T14:00:00.000Z",
            	"http://xapi.jisc.ac.uk/event_type_id": "1",
	    	"http://xapi.jisc.ac.uk/event_type_description": "Lecture", 
            	"http://xapi.jisc.ac.uk/event_max_count": 32,
            	"http://xapi.jisc.ac.uk/event_mandatory": 1,
       	 }
    },
		
```

### Context
Common entity identifier: Common entity identifier: [ContextD](/common_structures.md#contextd)


#### Entity Example:


``` javascript
 "context": {
     "instructor": {
            "objectType": "Agent",
            "account": {
                "name": "2",
                "homePage": "http://localhost/moodle"
            }
		},
		
	 "extensions": {
        "http://xapi.jisc.ac.uk/version": "1.0",
			"http://xapi.jisc.ac.uk/deviceLocation": {
			"type": "Feature",
			"geometry": {
				"type": "Point",
				"coordinates": [51.510531, -0.118930]
					},
				"properties": {
				"name": "University of Jisc"
				}
			},	
			
		"http://xapi.jisc.ac.uk/courseArea": {
                	"http://xapi.jisc.ac.uk/vle_mod_id": "LA101-200-2016S1-0",
			"http://xapi.jisc.ac.uk/uddModInstanceID": "LA101-200-2016S1-0",
               		 "id": "http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4"
            		}	
		}
    }
```


# Example
``` javascript
{
    "id": "12345678-1234-5678-1234-567812345678",
    "actor": {
        "objectType": "Agent",
        "name": "John Smith",
        "account": {
            "name": "2",
            "homePage": "https://courses.alpha.jisc.ac.uk/moodle"
        }
    },
    "verb": {
        "id": "http://adlnet.gov/expapi/verbs/attended",
        "display": {
            "en": "attended"
        }
    },
    "result": {
        "completion": true,
        "extensions": {
            "http://xapi.jisc.ac.uk/event_late": "1"
        }
    },
	
 "object": {
        "objectType": "Activity",
        "id": "http://wicketkeeper.poppleton.ac.uk/modules/2016/sem1/psy101/qlecture1",
        "definition": {
            "type": "http://xapi.jisc.ac.uk/lecture",
            "name": {
                "en": "Psychology 101 Introduction"
            },
            "description": {
                "en": "The first tutorial of psychology 101"
            }
		"extensions": {
            		"http://xapi.jisc.ac.uk/subType": "http://xapi.jisc.ac.uk/workshop"
			"http://xapi.jisc.ac.uk/starttime": "2016-02-05T10:00:00.000Z",
            		"http://xapi.jisc.ac.uk/endtime": "2016-02-05T14:00:00.000Z",
            		"http://xapi.jisc.ac.uk/event_type_id": "1",
	    		"http://xapi.jisc.ac.uk/event_timetabled": "1",
			"http://xapi.jisc.ac.uk/event_type_description": "Lecture", 
            		"http://xapi.jisc.ac.uk/event_max_count": "32",
            		"http://xapi.jisc.ac.uk/event_mandatory": "1"
			
            
        }
    },
		
    "context": {
        "extensions": {
            "http://xapi.jisc.ac.uk/courseArea": {
                "http://xapi.jisc.ac.uk/vle_mod_id": "LA101-200-2016S1-0",
		"http://xapi.jisc.ac.uk/uddModInstanceID": "LA101-200-2016S1-0",
                "id": "http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4"
            }
        },
        "instructor": {
            "objectType": "Agent",
            "account": {
                "name": "2",
                "homePage": "http://localhost/moodle"
            }
        }
    }
}

```

#intervention (Student performing activity) Recipe
Revision: 0.1 

## Purpose
This recipe records an intervention taking place. Interventions can be any learning activity, in this example an interview has taken place. The context is used to show that an intervention has taken place, particly the context.contextActivities.Catergory http://xapi.jisc.ac.uk/activities/intervention


## Draft Notes
The following previous candidates can be found:

[Candidate A](intervention_candidate_a.md)

[Candidate B](intervention_candidate_b.md)

[Candidate C](intervention_candidate_c.md)

Notes from the development chat can be found on [issue 130](https://github.com/jiscdev/xapi/issues/130)

In this draft the following approach has been taken:

- The actor is the student. The [sister recipe](intervention) describes system/tutor.
- Specific verbs are used in the verb to describe what the student did
- System information is added to the recipe. This helps the ' splitting of data pertaining to activity'.
- context.contextActivities 'tags' this as an intervention recipe
- ticket numbers are stored in the context
- The lost of verbs needs expanding by the community
- This example shows a tutor inteviewing a student. SID is suppied as the system but I do not know if that is realistic. Would SID record this has happened?

### Actor

The actor is student performing an activity.
 
#### Entity Example:
In this example it is the student who is doing something in response to an intervention.

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

The verb, depends on the intervention activity taking place. A list of verbs describing interventions and any related recipes can be found at the bottom of this recipe page (to be moved to vocab after draft). In this example the student attended a revision module. 

``` javascript
"verb": {
        "id": "http://adlnet.gov/expapi/verbs/attended",
        "display": {
            "en": "attended"
        }
    }
``` 
 

#### Entity Example:
The object defines the activity that has been completed. Examples of valid object.definition Activity object Types can be found in [the vocabulary](../vocabulary.md#30-object).
In this example it is a revision event.

``` javascript

"object":{
		"objectType":"Activity",
		"id":"http://wicketkeeper.poppleton.ac.uk/modules/2016/sem1/rev101/rlecture1",
		"definition":{
			"type":"http://activitystrea.ms/schema/1.0/event",
			"name":{
				"en":"Lecture"
			},
			"description":{
				"en":"Revision class"
				}
			},
			
		    "extensions":{
				"http://id.tincanapi.com/extension/planned-start-time": "2016-02-05T10:00:00.000Z",
				"http://xapi.jisc.ac.uk/extension/planned-end-time": "2016-02-05T14:00:00.000Z"
			}
			
		}
		
```

### Context

Common entity identifier: Context*

#### Entity Example:

context includes the version number of this recipe. 
context.contextActivies is of type category is tells us that this statement is related to intervention activities. (required if intervention)
context.platform is set to the platform tracking this activity. (optional)
context.extension.interventionId is any id or ticket number used by the system to identify the intervention this was a part of (optional)
context.tutor may be used to identify an involed tutor (optional)

``` javascript
"context": {
	"contextActivities":{
		"category": [{
			"objectType": "Activity",
			"id": "http://xapi.jisc.ac.uk/activities/intervention"
		}],
	},
	
    "platform": "Student Information Desk", 
	"extensions": {
		"http://xapi.jisc.ac.uk/recipeVersion" : "intervention.1",
		"http://xapi.jisc.ac.uk/interventionId":"38223",
		}
```

## Example

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
		"id": "http://adlnet.gov/expapi/verbs/attended",
		"display": {
			"en": "attended"
		}
	},
	"object": {
		"objectType": "Activity",
		"id": "http://wicketkeeper.poppleton.ac.uk/modules/2016/sem1/rev101/rlecture1",
		"definition": {
			"type": "http://activitystrea.ms/schema/1.0/event",
			"name": {
				"en": "Lecture"
			},
			"description": {
				"en": "Revision class"
			}
		}


	},

	"context": {
		"contextActivities": {
			"category": [{
				"objectType": "Activity",
				"id": "http://xapi.jisc.ac.uk/activities/intervention"
			}]
		},

		"platform": "Student Information Desk",
		"extensions": {
			"http://xapi.jisc.ac.uk/recipeVersion": "intervention.1",
			"http://xapi.jisc.ac.uk/interventionId": "38223",
			"http://xapi.jisc.ac.uk/logPlatform": "Student Information Desk"
		}



	},

	"id": "12345678-1234-5678-1234-567812345678"
}
```

## Intervention Verbs / Recipes
Verbs with their own recipes may be helpful.


### Attended
(attendence Recipe)[]

<table>
<tr><th align="left">Verb</th><td>Attended</td></tr>
<tr><th align="left">Description</th><td>Indicates the actor was present at a virtual or physical event or activity.</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://adlnet.gov/expapi/verbs/attended">http://adlnet.gov/expapi/verbs/attended</a> </td></tr>
<tr><th align="left">Recipe Example</th><td> <a href="recipes/attended.md#verb">Attended learning activity</a> </td></tr>
</table>



#intervention_candidate_c Recipe
Revision: 0.1 

DRAFT

## Purpose
This recipe records an intervention taking place, it is a record of an act by a person with an intention to help. This recipe uses sub statements.

## Draft Notes
In this draft the following approach is taken:

- The actor is the student and a context extension flags the fact the student has been acted upon
- Specific verbs are used in the verb to describe the intervention
- we use context to identify the umbrella
- The context includes an instructor that contains the instructor making the intervention


### Actor
 
#### Entity Example:
The actor is the student that the intervention involves.

``` Javascript
"actor": {
	"objectType": "Agent",
      "name": "Jimmy Smith",
      "account": {
         "name": "jsmith14",
         "homePage": "http://localhost/moodle"
      }
	}
```


### Verb

The verb, depends on the intervention taking place. A list of verbs describing interventions can be found at the bottom of this recipe (To be moved to vocab document). In this example the tutor annotated work. 

``` javascript
"verb": {
        "id": "http://risc-inc.com/annotator/verbs/annotated",
        "display": {
            "en": "Interviewed"
        }
    },
```


### Object

The object depends on the type of intervention and the verb used. In this case, object is the work that was annotated.


### Entity Example:
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

Context includes the tutor, an intervention category and the recipe version. A flag set to true shows that the acted is passive in the statement and has been acted upon.

``` javascript
"context": {
	"instructor": {
		"objectType": "Agent",
		"name": "Ray Keenan"
		"account": {
			"name": "rk345",
			"homePage": "http://moodle.jisc.ac.uk/users"
		},
	}
	"contextActivities":{
		"category": [{
			"objectType": "Activity",
			"id": "http://xapi.jisc.ac.uk/activities/intervention"
		}],
	}
	"extensions": {
		"http://xapi.jisc.ac.uk/recipeVersion" : "intervention.1",
		"http://xapi.jisc.ac.uk/actorActedUpon" : true,
  }
```

## Intervention Verbs

### Annotated
<table>
<tr><th align="left">Verb</th><td>Annotated</td></tr>
<tr><th align="left">Description</th><td>Indicates a new annotation has been added to a document. This verb may be used with PDFs, images, assignment submissions or any other type of document which may be annotated.</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://risc-inc.com/annotator/verbs/annotated">http://risc-inc.com/annotator/verbs/annotated</a> </td></tr>
<tr><th align="left">Recipe Example</th><td> <a href="recipes/intervention.md#verb">Intervention</a> </td></tr>
</table>


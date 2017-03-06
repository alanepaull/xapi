#intervention_candidate_b Recipe
Revision: 0.1 

## Purpose
This recipe records an intervention taking place, it is a record of an act by a person with an intention to help. 

## Draft Notes
In this draft the following approach is taken:

- The actor is the alerting system or tutor 
- Specific verbs are used in the verb entity to describe the intervention
- Object contains the student
- we use context to somehow identify the umbrella, for ease of querying

### Actor

The actor is an instructor or service creating the intervention. 
 
#### Entity Example A:
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
#### Entity Example B:
Another example shows a service that sent an intervention.

``` Javascript
"actor": {
	"objectType": "Agent",
      "name": "Student Information Desk",
      "account": {
         "name": "sid",
         "homePage": "http://sid.university.ac.uk"
      }
	}
```


### Verb

The verb, depends on the intervention taking place. A list of verbs describing interventions can be found at the bottom of this recipe page (to be moved to vocab after draft). In this example the tutor interviewed the student. 

``` javascript
"verb": {
        "id": "http://id.tincanapi.com/verb/interviewed",
        "display": {
            "en": "Interviewed"
        }
    },
```

 

### Object

In this case, object is the person that the intervention is acted upon. It is usually the student.

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

The context includes the version number of this recipe. It also groups this statement with other interventions

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
}
```

## Intervention Verbs

### Interviewed
<table>
<tr><th align="left">Verb</th><td>Interviewed</td></tr>
<tr><th align="left">Description</th><td>For use when one agent or group interviews another agent or group. It could be used for the purposes of hiring, creating news articles, shows, research, etc.</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://id.tincanapi.com/verb/interviewed">http://id.tincanapi.com/verb/interviewed</a> </td></tr>
<tr><th align="left">Recipe Example</th><td> <a href="recipes/intervention.md#verb">Intervention</a> </td></tr>
</table>

### Mentored
<table>
<tr><th align="left">Verb</th><td>Mentored</td></tr>
<tr><th align="left">Description</th><td>Indicates that that the actor has mentored the object. For instance, a manager mentoring an employee, or a teacher mentoring a student. </td></tr>
<tr><th align="left">IRI</th><td> <a href="http://id.tincanapi.com/verb/mentored">http://id.tincanapi.com/verb/mentored</a> </td></tr>
<tr><th align="left">Recipe Example</th><td> <a href="recipes/intervention.md#verb">Intervention</a> </td></tr>
</table>


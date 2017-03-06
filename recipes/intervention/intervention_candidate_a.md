# intervention_candidate_a Recipe
Revision: 0.1 

DRAFT

## Purpose
This recipe records an intervention taking place, it is a record of an act by a person with an intention to help. 

## Draft Notes 

- The actor is an instructor or service making the intervention
- A single verb is used in the verb to describe the fact this is an intervention
- The object is sub statement describing the intervention


### Actor
Common entity identifier: Common entity identifier: [ActorA](../common_structures.md#actora) 
 
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


#### Entity Example
The verb, intervene, describes an intervention by the actor on the object.

``` javascript
"verb": {
        "id": "http://xapi.jisc.ac.uk/intervene",
        "display": {
            "en": "intervene"
        }
    },
```


### Object
The object of the statement is of objectType substatement and describes the intervention that has been made. In this example the tutor who raised the intervention has interviewed the student.

A list of verbs can be found at the bottom of this recipe (To be moved to the vocab document after draft)


#### Entity Example

``` Javascript
  "object": {
        "objectType": "SubStatement",
        "actor" : {
            "objectType": "Agent",
			"name": "Ray Keenan",
			"account": {
				"name": "rkeenan12",
				"homePage": "http://localhost/moodle"
        },
        "verb" : { 
            "id":"ttp://id.tincanapi.com/verb/interviewed", 
            "display":{
                "en-US":"will visit"
            } 
        },
        "object": {
           "objectType": "Agent",
	   "name": "Joe Blogs",
	   "account": {
		"name": "Jblogs9",
		"homePage": "http://localhost/moodle"
        	},
            }
        }
```


### Context

Common entity identifier: Context*

#### Entity Example:

The context includes the version number of this recipe.

``` javascript
"context": {
  "extensions": {
    "http://xapi.jisc.ac.uk/recipeVersion" : "physical_presence0.1",
  }
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


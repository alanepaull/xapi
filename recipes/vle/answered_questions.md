# quiz_question_answered statement template

In this version the Moodle domain IRIs for subType are not definitive, but purely given as examples. Moodle domain experts will control these IRIs.

## Purpose
Use this template to create a specific Statement for a student answering 1 or more questions in a quiz, but not yet completing it.

## Definition

### Actor
The Actor entity is used to identify the individual that answered the question or questions.

#### Entity properties:
Common entity identifier:  ActorA, as defined on the [common structures](/common_structures.md#actora) page.

### Example:

``` Javascript
"actor": {
  "objectType": "Agent",
  "name": "John Smith",
  "account": {
    "name": "jsmith12",
    "homePage": "https://courses.alpha.jisc.ac.uk/moodle"
  }
}
```

### Verb
The Verb [answered](/vocabulary.md#verbs). It denotes the action of the Actor answering a question, where the Object is generally an activity representing the question or questions.

#### Entity properties:
Common entity identifier:  VerbA, as defined on the [common structures](/common_structures.md#verba) page.

### Example:

``` javascript
"verb": {
  "id": "http://adlnet.gov/expapi/verbs/answered",
  "display": {
    "en" : "answered"
  }
}
```

### Object

The Object identifies the question or questions.

### Entity properties:
<table>
	<tr><th>Property [cardinality]</th><th>Description</th><th>Value information</</th></tr>
	<tr>
		<td>object.objectType [1]</td>
		<td>The value must be "Activity".</td>
		<td>String, value must be "Activity".</td>
	</tr>
	<tr>
		<td>object.id [1]</td>
		<td>An identifier for the quiz</td>
		<td>iri</td>
	</tr>
	<tr>
		<td>object.definition.type [1]</td>
		<td>Indicates the type of the Object of the Statement. It is required and valid values are listed on the [vocabulary page](vocabulary.md#activity-types).</td>
		<td>iri</td>
	</tr>
	<tr>
		<td>object.definition.name [0..1]</td>
		<td>Optional object name</td>
		<td>string</td>
	</tr>
	<tr>
		<td>object.definition.correctResponsesPattern [1]</td>
		<td>The Correct Responses Pattern contains an array of response patterns. A learner's response will be considered correct if it matches any of the response patterns in that array. See the <a href="https://github.com/adlnet/xAPI-Spec/blob/master/xAPI-Data.md#response-patterns">xAPI spec for more details</a>.</td>
		<td>iri</td>
	</tr>
</table>


### Example

``` javascript
"object": {
  "id": "http://localhost/moodle/mod/quiz/view.php?id=10",
  "objectType": "Activity"
  "definition": {
		"correctResponsesPattern": [
			"false"
			],
		"interactionType": "true-false",
		"description": {
			"en": "Greener is a color"
		},
		"name": {
			"en": "Greener is a color"
		},
		"type": "http://adlnet.gov/expapi/activities/module"
	},

}

```

### Result

### Entity properties:

<table>
	<tr><th>Property [cardinality]</th><th>Description</th><th>Value information</</th></tr>
	<tr>
		<td>result.score.max [0..1]</td>
		<td>The highest possible score</td>
		<td>decimal number greater than min (if present)</td>
	</tr>
	<tr>
		<td>result.success [0..1]</td>
		<td>Indicates whether or not the attempt was successful.</td>
		<td>true or false</td>
	</tr>
	<tr>
		<td>result.completion [0..1]</td>
		<td>Indicates whether or not the Activity was completed.</td>
		<td>true or false</td>
	</tr
	>	<tr>
		<td>result.response [0..1]</td>
		<td>Instructor's or automatic feedback</td>
		<td>string (256)</td>
	</tr>
	<tr>
		<td>result.extensions.http://xapi.jisc.ac.uk/grade [0..1]</td>
		<td>Non-numerical assessment result</td>
		<td>string (256)</td>
	</tr>
</table>


### Example

``` javascript
 "result": {
      "response": "true",
      "completion": true,
      "success": false,
      "score": {
        "max": 1
      }
    },
```
	
### Context

#### Entity properties:

<table>
	<tr><th>Property [cardinality]</th><th>Description</th><th>Value information</</th></tr>
	<tr>
		<td>context.platform [1]</td>
		<td>The platform used in the experience of this learning activity. The value used should not change between platform upgrades and version changes and, should typically be a concise name by which the application is commonly known, for example "Moodle" or "Blackboard"</td>
		<td>string</td>
	</tr>	
	<tr>
		<td>context.extensions.version [0..1]</td>
		<td>Recommended, identifies the version of the Jisc xAPI profile found on the ReadMe page. <br/></td>
		<td>decimal</td>
	</tr>
	<tr>
		<td>context.extension.sessionId [0..1]</td>
		<td>The VLE session ID, or a suitably hashed version of it. A value should be provided if this information is available.</td>
		<td>string</td>
	<tr> 
		<td>context.extension.ip-address [1]</td>
		<td>client's IP address. An IPv4 address is recommended.</td>
		<td>ip address</td>
	<tr> 
		<td>context.extension.courseArea [0..1]</td>
		<td>The academic context in which this activity is situated (e.g. umbrella course, or parent area). This could be a UDD Module Instance ID or VLE Module ID.. More information can be found on the [vocabularies page](/vocabulary.md#course-area).</td>
		<td>JSON object</td>
	<tr>
	<tr> 
		<td>context.contextActivities [0..1]</td>
		<td>Set to Parent, since this is a statement about a question it has a quiz as its parent Activity. </td>
		<td>JSON object</td>
	<tr> 	
</table>

#### Example:
``` javascript
  "context": {
    
      "platform": "Moodle",
      	  
      "extensions": {
	"http://xapi&46;jisc&46;ac&46;uk/version": "x-2017-05-16",
	"http://xapi&46;jisc&46;ac&46;uk/sessionId": "Iye9OqwM9O", 
        "http://id&46;tincanapi&46;com/extension/ip-address": "0:0:0:0:0:0:0:1", 
        "http://xapi&46;jisc&46;ac&46;uk/courseArea": {
		"http://xapi&46;jisc&46;ac&46;uk/vle_mod_id": "Test1"
        	},
        },
        
      "contextActivities": {
        "parent": [
          {
            "id": "http://localhost/moodle/mod/quiz/view.php?id=10",
            "objectType": "Activity",
            "description": {
              "en": "A quiz"
              },
            "name": {
              "en": "mquiz"
              },
            "type": "http://xapi.jisc.ac.uk/vle/quiz"
              },
            "definition": {
              "extensions": {
                "http://xapi&46;jisc&46;ac&46;uk/subType": "http://xapi.jisc.ac.uk/vle/quiz"
              },
          }
        ]
      }
    },
```

## Full Example:

``` javascript

{
  "statement": {
     "actor": {
       "objectType": "Agent",
       "name": "John Smith",
       "account": {
         "name": "jsmith12",
         "homePage": "https://courses.alpha.jisc.ac.uk/moodle"
       }
     },
     
     "verb": {
       "id": "http://adlnet.gov/expapi/verbs/answered",
       "display": {
         "en" : "answered"
       }
     },
     
     "object": {
       "id": "http://localhost/moodle/mod/quiz/view.php?id=10",
       "objectType": "Activity"
       "definition": {
     		"correctResponsesPattern": [
     			"false"
     			],
     		"interactionType": "true-false",
     		"description": {
     			"en": "Greener is a color"
     		},
     		"name": {
     			"en": "Greener is a color"
     		},
     		"type": "http://adlnet.gov/expapi/activities/module"
     	}
     },
     
     "result": {
       "response": "true",
       "completion": true,
       "success": false,
       "score": {
         "max": 1
         }
     },
     
     "context": {  
       "platform": "Moodle",    	  
           "extensions": {
       "http://xapi&46;jisc&46;ac&46;uk/version": "x-2017-05-16",
       "http://xapi&46;jisc&46;ac&46;uk/sessionId": "Iye9OqwM9O", 
       "http://id&46;tincanapi&46;com/extension/ip-address": "0:0:0:0:0:0:0:1", 
       "http://xapi&46;jisc&46;ac&46;uk/courseArea": {
     	  "http://xapi&46;jisc&46;ac&46;uk/vle_mod_id": "Test1"
          },
       },
       "contextActivities": {
         "parent": [
           {
           "id": "http://localhost/moodle/mod/quiz/view.php?id=10",
           "objectType": "Activity",
           "description": {
             "en": "A quiz"
              },
           "name": {
             "en": "mquiz"
              },
           "type": "http://xapi.jisc.ac.uk/vle/quiz"
           },
           "definition": {
             "extensions": {
               "http://xapi&46;jisc&46;ac&46;uk/subType": "http://xapi.jisc.ac.uk/vle/quiz"
               },
             }
            ]
           }
         }

```
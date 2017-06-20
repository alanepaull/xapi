# question_assessed statement template
Based on statement template for vle_assignment_graded (assignment-graded.md). Differences relate to the question's position in relation to its parent quiz.

[Statement Template Changes](/version_changes.md#question_assessed)

## Purpose
This statement template describes a user receiving a grade, mark or other response to a quiz question.

Natural language example of a typical statement: "John Smith scored "Correct" for the first question in Quiz 1 (part of a module in his university Moodle VLE) and received immediate feedback."

Examples:

- [tbd]

## Definition

### Actor
The actor entity is used to identify the individual that is answering the question. It uses the Jisc profile common entity [ActorA](/common_structures.md#actora).

#### Entity properties:

<table>
<tr><th>Property</th><th>Description</th></tr>
<tr>
<td>actor.objectType [1]</td><td>Must have the value "Agent". Actors of type "Group" are not supported in the Jisc profile.</td>
</tr>
<tr>
<td>actor.name [0..1]</td><td>Full name of student.</td>
</tr>
<tr>
<td>	
actor.account [1] <br/>
actor.account.name [1] <br/>
actor.account.homepage [1] <br/>
</td>
<td>A JSON Object with <b>account.name</b> giving a system login id for the subject of the statement and <b>account.homepage</b> giving the URL of the home page of the application for which the login id applies.</td></tr>
</table>

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
The verb used in question_graded statement is [scored](/vocabulary.md#verbs). It describes the action of receiving an evaluation of an activity. It uses the Jisc common entity [VerbA](../common_structures.md#verba).

#### Entity properties:

<table>
	<tr><th>Property</th><th>Description</th></tr>
	<tr>
		<td>verb.id [1]</td>
		<td>An IRI that identifies the Verb. http://adlnet.gov/expapi/verbs/scored in this statement.</td>
	</tr>
	<tr>
		<td>verb.display [1]</td>
		<td>A human readable representation of Verb. It takes a RFC 5646 Language Tag. "scored" in this type of statement. </td>
	</tr>
</table>

``` javascript
"verb": {
        "id": "http://adlnet.gov/expapi/verbs/scored",
        "display": {
            "en": "scored"
        }
    },
``` 

### Result
The result entity is optional. It is used when feedback, including assessment feedback, is given when the question is answered. It uses the Jisc common entity [ResultB](../common_structures.md#resultb).


The result entity is optional and includes completion.

<table>
	<tr><th>Property [cardinality]</th><th>Description</th><th>Data type</th></tr>
	<tr>
		<td>result.score.scaled [0..1]</td>
		<td>The score related to the experience as modified by scaling and/or normalization</td>
<td>decimal number between -1 and 1, inclusive.</td>
	</tr>
	<tr>
		<td>result.score.raw [0..1]</td>
		<td>Unmodified score</td>
<td>decimal number between min and max (if present, otherwise unrestricted), inclusive</td>
	</tr>
	<tr>
		<td>result.score.min [0..1]</td>
		<td>The lowest possible score</td>
<td>decimal number less than max (if present)</td>
	</tr>
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

### Example:

```
"result": {
        "score": {
            "scaled": 0.25,
            "raw": 25,
            "min": 0,
            "max": 100
        },
		
        "success": false,
        "completion": true,
        "response": "Your answer should have been: The cow jumped over the moon."
         }

````

### Object

The object identifies the question being answered. It is based on the Jisc Profile common entity [ObjectA](../common_structures.md#objectA).

#### Entity properties:

<table>
	<tr><th>Property</th><th>Description</th></tr>
	<tr>
		<td>object.objectType [1]</td>
		<td>The value must be "Activity".</td>
	</tr>
	<tr>
		<td>object.id [1]</td>
		<td>An identifier for the question.</td>
	</tr>
		<tr>
		<td>object.definition.type [1]<br />
	object.definition.name [0..1]<br />
	object.definition.extensions.http://xapi.jisc.ac.uk/subType [0..1]</td>
		<td>A JSON object comprising both standard xAPI attributes and the Jisc profile 'subType' extension.<br/>
    The <b>type</b> indicates the type of the object of the statement. It is required and for this statement the value must be http://adlnet.gov/expapi/activities/question.<br/>
    The <b>name</b> is optional, but gives a helpful human readable description.<br/>
    The <b>subType</b> extension is used to further differentiate the question by qualifying the object.definition.type with a type for the question. In this statement the value of subType is drawn from a domain specific vocabulary dependent on the platform.<br /></td>
	</tr>
</table>

Example:

``` javascript

"object":{
		"objectType":"Activity",
		"id":"http://moodle.data.alpha.jisc.ac.uk/mod/quiz/attempt.php?attempt=1",
		"definition":{
			"type":"http://adlnet.gov/expapi/activities/question",
			"name":{
				"en":"Sample question from quiz1"
			},
		  	  "extensions":{
				"http://xapi.jisc.ac.uk/subType": "http://moodle.xapi.jisc.ac.uk/multiple-choice"
			}
		}
		
```

### Context
Context is used to describe the quiz within which the question sits. If the device supports it, session Ids and ip-addresses can be recorded. The contexct for this statement is based on ContextB, as defined on the [common structures](/common_structures.md#contextB) page, but contextActivities.parent is used to denote the quiz of which the question forms a part.

#### Entity properties:
<table>
<tr><th>Property</th><th>Description</th></tr>
	<tr>
		<td>context.contextActivities [0..1]<br />
		context.contextActivities.parent [1]
		</td>
		<td>An optional property that holds a mandatory parent property. It allows a statement about a question to be associated with the quiz of which it forms a part.  The 'parent' property has an <a href="#objecta">ObjectA</a> as its value.</td>
	</tr>
	<tr><td>context.platform [1]</td>
	<td>The platform used in the experience of this learning activity. The value used should not change between platform upgrades and version changes and should typically be a concise name by which the application is commonly known, for example "Moodle" or "Blackboard"</td></tr>
	<tr><td>context.extensions.version [0..1]
		 context.extension.sessionId [0..1]
		 context.extension.ip-address [1]
		 context.extension.courseArea [0..1]
		 </td>
		<td>Four extensions are provided for, with IRIs as defined on the <a href="vocabulary.md#41-context-extensions">vocabularies page</a>.
  	  The <b>sessionID</b> extension is the VLE session ID, or a suitably hashed version of it. A value should be provided if this information is available.<br/>
    The <b>ip-address</b> is used to identify the client's IP address. An IPv4 address is recommended.<br/>
    The <b>version</b> extension is recommended, and identifies the version of the Jisc xAPI profile found on the ReadMe page.<br/>
	The <b>courseArea</b> identifies Umbrella course/parent area by its home page URI. It is optional.
		</td></tr></table>

### Example:

``` javascript
"context": {
	"contextActivities":{
		  "parent":[
		    {
		  	"objectType":"Activity",
		        "id":"http://moodle.data.alpha.jisc.ac.uk/mod/quiz/quiz1",
		        "definition":{
		        	"type":"http://xapi.jisc.ac.uk/vle/quiz",
		                "name": {
		                	  "en":"xAPI review quiz"
		                	},
		                "description":{
	                	  "en":"Quiz for xAPI Basics course for Learning Analytics enthusiasts"
		                        }
		                    }
		                }
		            ]
            },
        "platform": "Moodle",
        "extensions": {
		
      		"http://xapi.jisc.ac.uk/courseArea": {
      		 	"http://xapi.jisc.ac.uk/vle_mod_id": "LA101",
				"http://xapi.jisc.ac.uk/uddModInstanceID": "LA101-200-2016S1-0",
                "id": "http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4"
				},
			"http://xapi.jisc.ac.uk/sessionId":"32456891",
         	"http://id.tincanapi.com/extension/ip-address": "10.3.3.48",
			"http://xapi.jisc.ac.uk/version" : "1.0"
			}
		}
```

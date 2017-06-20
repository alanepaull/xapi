# quiz_question_viewed statement template
Based on generic statement template resource_viewed (view.md).
In this version the Moodle domain IRIs for subType are not definitive, but purely given as examples. Moodle domain experts will control these IRIs.

## Purpose
Use this template to create a specific statement for a student looking at a quiz or a question in a quiz.

Natural language example of a typical statement: "John Smith viewed the first question in Quiz 1 (part of a module in his university Moodle VLE)."

Examples:

- [tbd]

## Definition

### Actor
The actor entity is used to identify the individual that is viewing the quiz or question. It uses the Jisc profile common entity [ActorA](/common_structures.md#actora).

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
The verb used in view statements is [viewed](../vocabulary.md#verbs). It denotes the action of the user requesting the resource that the user wishes to view. It uses the Jisc common entity [VerbA](../common_structures.md#verba). 

#### Entity properties:

<table>
	<tr><th>Property</th><th>Description</th></tr>
	<tr>
		<td>verb.id [1]</td>
		<td>An IRI that identifies the Verb. http://id.tincanapi.com/verb/viewed in viewed statements.</td>
	</tr>
	<tr>
		<td>verb.display [1]</td>
		<td>A human readable representation of Verb. It takes a RFC 5646 Language Tag. "viewed" in this type of statement. </td>
	</tr>
</table>

### Example:

``` javascript
"verb": {
  "id": "http://id.tincanapi.com/verb/viewed",
  "display": {
    "en" : "viewed"
  }
}
```

### Object

The object identifies the quiz or question being viewed. It uses the Jisc Profile common entity [ObjectA](../common_structures.md#objectA).


#### Object Entity properties:

<table>
	<tr><th>Property</th><th>Description</th></tr>
	<tr>
		<td>object.objectType [1]</td>
		<td>The value must be "Activity".</td>
	</tr>
	<tr>
		<td>object.id [1]</td>
		<td>An identifier for the quiz or question.</td>
	</tr>
		<tr>
		<td>object.definition.type [1]<br />
	object.definition.name [0..1]<br />
	object.definition.extensions.http://xapi.jisc.ac.uk/subType [0..1]</td>
		<td>A JSON object comprising both standard xAPI attributes and the Jisc profile 'subType' extension.<br/>
    The <b>type</b> indicates the type of the object of the statement. It is required and for this statement the value must be either http://xapi.jisc.ac.uk/vle/quiz or http://adlnet.gov/expapi/activities/question.<br/>
    The <b>name</b> is optional, but gives a helpful human readable description.<br/>
    The <b>subType</b> extension is used to further differentiate the activity by qualifying the object.definition.type. In this statement the value of subType must be 1 of: http://xapi.jisc.ac.uk/vle/quiz for viewing a quiz, or http://adlnet.gov/expapi/activities/question for viewing a question, or a domain specific subType indicating a type of quiz or question (see specific vocabulary for the domain of the application).<br /></td>
	</tr>
</table>

### Example of viewing a quiz

``` javascript
"object": {
  "objectType": "Activity",
  "id": "http://moodle.data.alpha.jisc.ac.uk/mod/quiz/quiz1",
  "definition": {
    "type": "http://xapi.jisc.ac.uk/vle/quiz",
    "name": {
      "en": "Sample quiz"
    },
    "extensions": {
      "http://xapi.jisc.ac.uk/subType": "http://xapi.jisc.ac.uk/vle/quiz"
    }
  }
}

```

### Example of viewing a multiple-choice question in Moodle

``` javascript
"object": {
  "objectType": "Activity",
  "id": "http://moodle.data.alpha.jisc.ac.uk/mod/quiz/attempt.php?attempt=1",
  "definition": {
    "type": "http://adlnet.gov/expapi/activities/question",
    "name": {
      "en": "Sample question from quiz1"
    },
    "extensions": {
      "http://xapi.jisc.ac.uk/subType": "http://moodle.xapi.jisc.ac.uk/multiple-choice"
    }
  }
}

### Context
Context is used to describe the module within which the quiz sits, or the quiz within which the question sits. If the device supports it, session Ids and ip-addresses can be recorded. Common entity identifier: For quiz - ContextA, as defined on the [common structures](/common_structures.md#contexta) page; for question - ContextB, as defined on the [common structures](/common_structures.md#contextB) page; ContextB enables the statement to identify the quiz as well as the question.

#### Entity properties:
<table>
<tr><th>Property</th><th>Description</th></tr>
	<tr>
		<td>For questions only: <br />
		context.contextActivities [0..1]<br />
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

### Example for viewing quiz:

``` javascript
"context": {
        "platform": "Moodle",
        "extensions": {
	  "http://xapi.jisc.ac.uk/courseArea": {
	  	"http://xapi.jisc.ac.uk/vle_mod_id": "LA101",
	  	"http://xapi.jisc.ac.uk/uddModInstanceID": "LA101"
            	"id":"http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4"
		},		
	"http://xapi.jisc.ac.uk/sessionId": "32456891",
	"http://id.tincanapi.com/extension/ip-address": "10.3.3.48",
	"http://xapi.jisc.ac.uk/version" : "1.0"
	  }
        }
```

### Example for viewing question:

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
	  	"http://xapi.jisc.ac.uk/uddModInstanceID": "LA101"
            	"id":"http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4"
		},		
	"http://xapi.jisc.ac.uk/sessionId": "32456891",
	"http://id.tincanapi.com/extension/ip-address": "10.3.3.48",
	"http://xapi.jisc.ac.uk/version" : "1.0"
	  }
        }
```